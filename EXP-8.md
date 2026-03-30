# HAMMING WINDOW BASED FIR FILTER DESIGN
# AIM :
To design a Low Pass FIR filter using Hamming Window and study its frequency characteristics.
# THEORY:

Hamming window is defined as:

w(n)=0.54-0.46cos⁡(2πn/N)

Characteristics:
Reduced side lobes

Better stopband attenuation (~41 dB)

Slightly wider main lobe than rectangular

Reduced ripple

Design Equation:

h(n)=h_d (n)⋅w(n)

Where hd(n) is ideal impulse response.

# ALGORITHM:
1.	Choose N and ωc
2.	Compute ideal impulse response
3.	Generate Hamming window
4.	Multiply and obtain h(n)
5.	Plot magnitude & phase

# MATLAB CODE :
~~~
clc;
clear;
close all;

N = 20;
wc = 0.4*pi;
n = 0:N;
alpha = N/2;

hd = sin(wc*(n-alpha))./(pi*(n-alpha));
hd(alpha+1) = wc/pi;

w = hamming(N+1)';
h = hd.*w;

freqz(h,1);
title('FIR using Hamming Window');
~~~
# OUTPUT GRAPH :
<img width="678" height="479" alt="image" src="https://github.com/user-attachments/assets/a9e6e362-e61d-462c-ace5-f1679e2b1822" />

# RESULT :
The FIR filter was designed using Hamming window .

