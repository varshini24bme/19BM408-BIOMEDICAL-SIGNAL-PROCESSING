# DESIGN OF DIGITAL CHEBYSHEV LOW PASS FILTER USING BILINEAR TRANSFORMATION

# AIM:
To design a digital Chebyshev low pass filter using the bilinear transformation method in MATLAB satisfying the following constraints:

0.8≤∣H(ω)∣≤1.0;0≤ω≤0.2π

∣H(ω)∣≤0.2;0.32π≤ω≤π
Assume sampling period T=1second.

# APPARATUS REQUIRED :

MATLAB software
  
Computer system
  
Given Specifications

Passband edge frequency:

ω_p=0.2π

Stopband edge frequency:

ω_s=0.32π

Passband ripple:

A_p=-20〖log⁡〗_10 (0.8)≈1.94" dB"

Stopband attenuation:

A_s=-20〖log⁡〗_10 (0.2)≈13.98" dB"

Sampling period:

T=1" second"

# Theory:

Chebyshev filters provide a sharper transition between passband and stopband compared to Butterworth filters but allow ripples in the passband (Type-I).
The bilinear transformation converts an analog filter into a digital filter using:

s=2/T  (1-z^(-1))/(1+z^(-1) )

Frequency pre-warping is required to compensate for frequency warping introduced by bilinear transformation.
Steps involved:
Prewarp the digital frequencies.
Design an analog Chebyshev filter.
Convert it into a digital filter using bilinear transformation.
Plot magnitude and phase response.

# ALGORITHM :

1)Specify passband and stopband edge frequencies.

2)Convert digital frequencies into analog frequencies using pre-warping.

3)Calculate filter order using Chebyshev approximation.

4)Design analog Chebyshev low pass filter.

5)Convert analog filter to digital filter using bilinear transformation.

6)Plot frequency response using freqz.

7)Verify that the designed filter meets the given constraints.

# MATLAB CODE :
~~~
clc;
clear;
close all;

T = 1;   % Sampling period

wp = 0.2*pi;    % Passband frequency
ws = 0.32*pi;   % Stopband frequency

Ap = -20*log10(0.8);   % Passband ripple in dB
As = -20*log10(0.2);   % Stopband attenuation in dB

% Pre-warping
Wp = (2/T)*tan(wp/2);
Ws = (2/T)*tan(ws/2);

% Order and cutoff frequency
[N, Wn] = cheb1ord(Wp, Ws, Ap, As, 's');

% Analog Chebyshev filter
[b, a] = cheby1(N, Ap, Wn, 's');

% Bilinear transformation
[bd, ad] = bilinear(b, a, 1/T);

% Frequency response
[H, w] = freqz(bd, ad, 1024);

% Plot magnitude response
figure;
plot(w/pi, abs(H));
grid on;
xlabel('Normalized Frequency (\times\pi rad/sample)');
ylabel('Magnitude |H(w)|');
title('Magnitude Response of Digital Chebyshev LPF');

% Plot phase response
figure;
plot(w/pi, angle(H));
grid on;
xlabel('Normalized Frequency (\times\pi rad/sample)');
ylabel('Phase (radians)');
title('Phase Response of Digital Chebyshev LPF');
~~~
# OUTPUT GRAPH :
<img width="705" height="479" alt="image" src="https://github.com/user-attachments/assets/e2d0d8e8-afa7-4810-83c5-ca8f75ff632e" />
<img width="716" height="483" alt="image" src="https://github.com/user-attachments/assets/2aa43f81-4cc7-4ce0-8ba7-50bc82911a6e" />

# RESULT:
A digital Chebyshev low pass filter satisfying the given specifications was successfully designed using the bilinear transformation method and its frequency response was verified using MATLAB.
