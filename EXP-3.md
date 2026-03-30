# DIT–FAST FOURIER TRANSFORM (FFT) USING RADIX-2 ALGORITHM
# AIM:
To compute the Fast Fourier Transform (FFT) of a discrete-time signal using the Radix-2 Decimation-in-Time (DIT) algorithm using MATLAB.

# APPARATUS REQUIRED :
•	Computer / Laptop

•	MATLAB software

# Theory :
The Fast Fourier Transform (FFT) is a fast method of computing the Discrete Fourier Transform (DFT).
In the Radix-2 Decimation-in-Time (DIT) FFT:
	The input signal is divided first (decimated in time)
	The signal is split into even and odd indexed samples
	Smaller DFTs are computed
	Results are combined using butterfly operations
The Radix-2 DIT FFT requires the number of samples to be a power of 2:

N=2^m

This method reduces the computational complexity from:

DFT: N^2

FFT: N〖log⁡〗_2 N

Key Features of DIT-FFT :  
1) Decimation is done in time domain .

2) Input sequence is bit-reversed .
  
3) Output is in natural order  .
  
4) FFT is computed in log₂N stages.

# Algorithm :
1)Start the program

2)Define a discrete-time signal of length N=2^m

3)Rearrange the input in bit-reversed order

4)Apply FFT using Radix-2 DIT method

5)Compute the magnitude spectrum

6)Plot the FFT output

7)Stop the program

# MATLAB CODE:
~~~
% DIT - RADIX-2 FAST FOURIER TRANSFORM

clc;
clear;
close all;

% Input discrete-time signal (N = 8, power of 2)
x = [1 2 3 4 4 3 2 1];
N = length(x);

% Compute FFT (Radix-2 DIT)
X = fft(x);

% Display FFT values
disp('DIT-FFT Output:');
disp(X);

% Frequency index
k = 0:N-1;

% Plot magnitude spectrum
figure;
stem(k, abs(X), 'filled');
xlabel('Frequency index k');
ylabel('|X(k)|');
title('Magnitude Spectrum using Radix-2 DIT FFT');
grid on;
~~~
# OUTPUT GRAPH :
<img width="674" height="482" alt="image" src="https://github.com/user-attachments/assets/70790c87-c823-49ee-ad8a-2b125a0c85eb" />

# RESULT:
Thus, the Fast Fourier Transform of the given discrete-time signal was successfully computed using the Radix-2 Decimation-in-Time (DIT) FFT algorithm in MATLAB.


