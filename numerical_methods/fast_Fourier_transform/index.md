---
layout: default
title: 快速傅里叶变换
---

快速傅里叶变换的C++&CUDA实现
```CUDA
#include "cuda_runtime.h"
#include "device_launch_parameters.h"
#include <cmath>
#include <float.h>

#define PI 3.141592741f

template<class T> __global__ void Device_memory_set(T* g, T value, unsigned int size)
{
	unsigned int i = blockDim.x * blockIdx.x + threadIdx.x;
	if (i >= size) return;
	g[i] = value;
}

template<class T> class Data_host_device
{
public:
	Data_host_device() :
		c(nullptr),
		g(nullptr),
		rows(0),
		columns(0)
	{

	}

	~Data_host_device()
	{

	}

	void Host_malloc(unsigned int iRows, unsigned int iColumns = 1)
	{
		if (nullptr != c || 0 == iRows * iColumns || (nullptr != g && (rows != iRows || columns != iColumns))) return;
		rows = iRows;
		columns = iColumns;
		c = (T*)malloc(size() * sizeof(T));
	}

	void Device_malloc(unsigned int iRows, unsigned int iColumns = 1)
	{
		if (nullptr != g || 0 == iRows * iColumns || (nullptr != c && (rows != iRows || columns != iColumns))) return;
		rows = iRows;
		columns = iColumns;
		if (cudaSuccess != cudaMalloc((void**)&g, size() * sizeof(T))) Device_clear();
	}

	void Host_set_value(T value, unsigned int begin = 0, unsigned int end = UINT_MAX)
	{
		if (nullptr == c) return;
		end = end < size() ? end : size();
		for (unsigned int i = begin; i < end; i++)
		{
			c[i] = value;
		}
	}

	void Device_set_value(T value, unsigned int begin = 0, unsigned int end = UINT_MAX)
	{
		if (nullptr == g) return;
		end = end < size() ? end : size();
		if (begin >= end) return;
		unsigned int threads_per_blocks = 256;
		unsigned int blocks_per_grids = (end - begin + threads_per_blocks - 1) / threads_per_blocks;
		Device_memory_set <<< blocks_per_grids, threads_per_blocks >>> (&g[begin], value, end - begin);
		if (cudaSuccess != cudaGetLastError()) Device_clear();
	}

	void Memcpy_host_to_device(unsigned int begin = 0, unsigned int end = UINT_MAX)
	{
		if (nullptr == c) return;
		end = end < size() ? end : size();
		if (begin >= end) return;
		if (nullptr == g) Device_malloc(rows, columns);
		if (cudaSuccess != cudaMemcpy(&g[begin], &c[begin], (end - begin) * sizeof(T), cudaMemcpyHostToDevice)) Clear();
	}

	void Memcpy_device_to_host(unsigned int begin = 0, unsigned int end = UINT_MAX)
	{
		if (nullptr == g) return;
		end = end < size() ? end : size();
		if (begin >= end) return;
		if (nullptr == c) Host_malloc(rows, columns);
		if (cudaSuccess != cudaMemcpy(&c[begin], &g[begin], (end - begin) * sizeof(T), cudaMemcpyDeviceToHost)) Clear();
	}

	void Memcpy_host_to_host(const T* host_ptr, unsigned int begin = 0, unsigned int end = UINT_MAX)
	{
		if (nullptr == c || nullptr == host_ptr) return;
		end = end < size() ? end : size();
		if (begin >= end) return;
		memcpy(&c[begin], host_ptr, (end - begin) * sizeof(T));
	}

	void Memcpy_device_to_device(const T* dev_ptr, unsigned int begin = 0, unsigned int end = UINT_MAX)
	{
		if (nullptr == g || nullptr == dev_ptr) return;
		end = end < size() ? end : size();
		if (begin >= end) return;
		if (cudaSuccess != cudaMemcpy(&g[begin], dev_ptr, (end - begin) * sizeof(T), cudaMemcpyDeviceToDevice)) Device_clear();
	}

	void Memcpy(const Data_host_device<T>& other, unsigned int begin = 0, unsigned int end = UINT_MAX)
	{
		Memcpy_host_to_host(other.c, begin, end);
		Memcpy_device_to_device(other.g, begin, end);
	}

	void Host_clear()
	{
		if (nullptr == c) return;
		free(c);
		c = nullptr;
		if (nullptr == g) rows = columns = 0;
	}

	void Device_clear()
	{
		if (nullptr == g) return;
		cudaFree(g);
		g = nullptr;
		if (nullptr == c) rows = columns = 0;
	}

	void Clear()
	{
		Host_clear();
		Device_clear();
	}

	T& hat(unsigned int rid, unsigned int cid = 0)
	{
		return c[rid * columns + cid];
	}

	__device__ T& dat(unsigned int rid, unsigned int cid = 0)
	{
		return g[rid * columns + cid];
	}

	__host__ __device__ unsigned int size() const
	{
		return rows * columns;
	}

	__host__ __device__ unsigned int row() const
	{
		return rows;
	}

	__host__ __device__ unsigned int column() const
	{
		return columns;
	}

private:
	T* c;
	T* g;
	unsigned int rows;
	unsigned int columns;
};

class Complex
{
public:
	__host__ __device__ Complex() :
		R(0),
		I(0)
	{

	}

	__host__ __device__ Complex(float real, float imag) :
		R(real),
		I(imag)
	{

	}

	__host__ __device__ ~Complex()
	{

	}

	__host__ __device__ Complex operator = (Complex c)
	{
		R = c.R;
		I = c.I;
		return *this;
	}

	__host__ __device__ void operator += (Complex& c)
	{
		R += c.R;
		I += c.I;
	}

	__host__ __device__ void operator -= (Complex& c)
	{
		R -= c.R;
		I -= c.I;
	}

	__host__ __device__ void operator *= (Complex& c)
	{
		float r = R * c.R - I * c.I;
		float i = R * c.I + I * c.R;
		R = r;
		I = i;
	}

	__host__ __device__ void operator /= (Complex& c)
	{
		float w = c.R * c.R + c.I * c.I;
		if (w + 1 == 1)
		{
			R = FLT_MAX;
			I = FLT_MAX;
			return;
		}
		float r = (R * c.R + I * c.I) / w;
		float i = (I * c.R - R * c.I) / w;
		R = r;
		I = i;
	}

	__host__ __device__ Complex operator + (Complex& c) const
	{
		return Complex(R + c.R, I + c.I);
	}

	__host__ __device__ Complex operator - (Complex& c) const
	{
		return Complex(R - c.R, I - c.I);
	}

	__host__ __device__ Complex operator * (Complex& c) const
	{
		return Complex(R * c.R - I * c.I, R * c.I + I * c.R);
	}

	__host__ __device__ Complex operator / (Complex& c) const
	{
		float w = c.R * c.R + c.I * c.I;
		if (w + 1 != 1) return Complex((R * c.R + I * c.I) / w, (I * c.R - R * c.I) / w);
		else return Complex(DBL_MAX, DBL_MAX);
	}

	__host__ __device__ Complex cpow(int n) const
	{
		float a = atan2(I, R);
		float r = exp(n * log(sqrt(R * R + I * I)));
		return Complex(r * cos(n * a), r * sin(n * a));
	}

	__host__ __device__ Complex croot(int n, Complex* p) const
	{
		float a = atan2(I, R);
		float r = exp(log(sqrt(R * R + I * I)) / n);
		for (int k = 0; k < n; ++k)
		{
			float t = (k * 2. * PI + a) / n;
			p[k] = { r * cos(t), r * sin(t) };
		}
		return p[n - 1];
	}

	__host__ __device__ Complex cexp() const
	{
		return Complex(exp(R) * cos(I), exp(R) * sin(I));
	}

	__host__ __device__ Complex clog() const
	{
		return Complex(log(sqrt(I * I + R * R)), atan2(I, R));
	}

	__host__ __device__ Complex csin() const
	{
		return Complex(sin(R) * (exp(I) + exp(-I)) / 2, cos(R) * (exp(I) - exp(-I)) / 2);
	}

	__host__ __device__ Complex ccos() const
	{
		return Complex(cos(R) * (exp(-I) + exp(I)) / 2, sin(R) * (exp(-I) - exp(I)) / 2);
	}

	__host__ __device__ float cfabs() const
	{
		return sqrt(R * R + I * I);
	}

	__host__ __device__ float cangle() const
	{
		return atan2(I, R);
	}

	float R;
	float I;
};

__global__ void Calculate_w(Data_host_device<Complex> w, Complex w0)
{
	unsigned int i = blockDim.x * blockIdx.x + threadIdx.x;
	if (i >= w.size()) return;
	w.dat(i) = w0.cpow(i);
}

__global__ void Calculate_A(Data_host_device<Complex> A1, Data_host_device<Complex> A2, Data_host_device<Complex> w, unsigned int p, unsigned int q)
{
	unsigned int temp0 = 1 << (p - 1);
	unsigned int temp1 = 1 << q;
	unsigned int temp2 = 1 << (q - 1);
	int k = blockIdx.x * blockDim.x + threadIdx.x;
	int j = blockIdx.y * blockDim.y + threadIdx.y;
	if (k >= temp0 / temp2 || j >= temp2) return;
	A2.dat(k * temp1 + j) = A1.dat(k * temp2 + j) + A1.dat(k * temp2 + j + temp0);
	A2.dat(k * temp1 + j + temp2) = (A1.dat(k * temp2 + j) - A1.dat(k * temp2 + j + temp0)) * w.dat(k * temp2);
}

__global__ void Divide_N(Data_host_device<Complex> A2)
{
	unsigned int i = blockDim.x * blockIdx.x + threadIdx.x;
	if (i >= A2.size()) return;
	A2.dat(i) /= Complex{ float(A2.size()), 0. };
}

class Fast_Fourier_transform
{
public:
	Fast_Fourier_transform()
	{

	}

	Fast_Fourier_transform(Data_host_device<Complex>& x)
	{
		Set_x(x);
	}

	~Fast_Fourier_transform()
	{
		x_.Clear();
		A1_.Clear();
		A2_.Clear();
		w_.Clear();
	}

	void Set_x(Data_host_device<Complex>& x)
	{
		unsigned int N = x.size();
		if (0 == N || 0 != (N & (N - 1))) return;
		x_.Clear();
		x_.Host_malloc(N);
		x_.Memcpy(x);
		x_.Memcpy_host_to_device();
		A1_.Clear();
		A2_.Clear();
		w_.Clear();
	}

	void Transform_GPU(const bool not_inverse = true)
	{
		unsigned int N = x_.size();
		if (0 == N || 0 != (N & (N - 1))) return;
		A1_.Device_malloc(N);
		A2_.Device_malloc(N);
		w_.Device_malloc(N >> 1);

		A1_.Memcpy(x_);
		const Complex w = not_inverse ? Complex{ 0.f, -2.f * PI / N }.cexp() : Complex{ 0.f, 2.f * PI / N }.cexp();
		dim3 threads_per_blocks(256);
		dim3 num_Blocks((w_.size() + threads_per_blocks.x - 1) / threads_per_blocks.x);
		Calculate_w <<< num_Blocks, threads_per_blocks >>> (w_, w);
		if (cudaSuccess != cudaGetLastError()) goto ERROR;

		unsigned int p = log2(N);
		threads_per_blocks = { 16, 16 };
		for (unsigned int q = 1; q <= p; q++)
		{
			num_Blocks = { ((1 << (p - q)) + threads_per_blocks.x - 1) / threads_per_blocks.x, ((1 << (q - 1)) + threads_per_blocks.y - 1) / threads_per_blocks.y };
			if (1 == q % 2) Calculate_A <<< num_Blocks, threads_per_blocks >>> (A1_, A2_, w_, p, q);
			else Calculate_A <<< num_Blocks, threads_per_blocks >>> (A2_, A1_, w_, p, q);
			if (cudaSuccess != cudaGetLastError()) goto ERROR;
		}
		if (0 == p % 2) A2_.Memcpy(A1_);

		if (not_inverse)
		{
			threads_per_blocks = { 256 };
			num_Blocks = { (A2_.size() + threads_per_blocks.x - 1) / threads_per_blocks.x };
			Divide_N <<< num_Blocks, threads_per_blocks >>> (A2_);
			if (cudaSuccess != cudaGetLastError()) goto ERROR;
		}

		if (cudaSuccess != cudaDeviceSynchronize()) goto ERROR;
		return;

	ERROR:
		A1_.Clear();
		A2_.Clear();
		w_.Clear();
	}

	void Transform_CPU(const bool not_inverse = true)
	{
		unsigned int N = x_.size();
		if (0 == N || 0 != (N & (N - 1))) return;
		A1_.Host_malloc(N);
		A2_.Host_malloc(N);
		w_.Host_malloc(N >> 1);

		A1_.Memcpy(x_);
		const Complex w = not_inverse ? Complex{ 0.f, -2.f * PI / N }.cexp() : Complex{ 0.f, 2.f * PI / N }.cexp();
		for (unsigned int i = 0; i < w_.size(); i++) w_.hat(i) = w.cpow(i);

		unsigned int p = log2(N);
		unsigned int temp = 1 << (p - 1);
		for (unsigned int q = 1; q <= p; q++)
		{
			unsigned int temp1 = 1 << q;
			unsigned int temp2 = 1 << (q - 1);
			unsigned int k_up_bound = temp / temp2;
			unsigned int j_up_bound = temp2;
			Data_host_device<Complex>* p1 = (1 == q % 2) ? &A1_ : &A2_;
			Data_host_device<Complex>* p2 = (1 == q % 2) ? &A2_ : &A1_;
			for (unsigned int k = 0; k < k_up_bound; k++)
			{
				for (unsigned int j = 0; j < j_up_bound; j++)
				{
					p2->hat(k * temp1 + j) = p1->hat(k * temp2 + j) + p1->hat(k * temp2 + j + temp);
					p2->hat(k * temp1 + j + temp2) = (p1->hat(k * temp2 + j) - p1->hat(k * temp2 + j + temp)) * w_.hat(k * temp2);
				}
			}
		}
		if (0 == p % 2) A2_.Memcpy(A1_);

		if (not_inverse)
		{
			for (unsigned int i = 0; i < N; i++)
			{
				A2_.hat(i) /= Complex{ float(N), 0. };
			}
		}
	}

	void Get_y(Data_host_device<Complex>& y)
	{
		unsigned int N = x_.size();
		if (0 == N || 0 != (N & (N - 1))) return;
		y.Clear();
		y.Host_malloc(N);
		y.Device_malloc(N);
		y.Memcpy(A2_);
	}

private:
	Data_host_device<Complex> x_;
	Data_host_device<Complex> A1_;
	Data_host_device<Complex> A2_;
	Data_host_device<Complex> w_;
};
```

* * *

[上一级](./../index.html)
