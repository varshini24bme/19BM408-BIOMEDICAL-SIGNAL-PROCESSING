# RECTANGULAR WINDOW BASED FIR FILTER DESIGN
# AIM :
To design a Low Pass FIR filter using Rectangular Window and analyze its magnitude and phase response using MATLAB.
# Theory :
Rectangular Window
The Rectangular window is defined as:
        w(n)=1≤n≤N
Characteristics:
Narrowest main lobe

Highest side lobes

High ripple (Gibbs phenomenon)

Sharp transition width

It simply truncates the ideal impulse response.

Design Equations
Ideal Low Pass Impulse Response:

h_d (n)=(sin⁡ω_c (n-α))/(π(n-α))

Where:

α=N/2

Actual filter:

h(n)=h_d (n)⋅w(n)

# ALGORITHM :
1.	Choose filter order N
2.	Choose cutoff frequency ωc
3.	Generate ideal impulse response
4.	Generate rectangular window
5.	Multiply both
6.	Plot frequency response

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
w = rectwin(N+1)';
h = hd.*w;
freqz(h,1);
title('FIR using Rectangular Window');
~~~
# OUTPUT GRAPH :
<img width="684" height="483" alt="image" src="https://github.com/user-attachments/assets/0ad065a6-1020-42fc-9aff-48234e45dbcc" />

# RESULT :
The FIR filter was designed using Rectangular window.
