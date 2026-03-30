# DESIGN OF DIGITAL BUTTERWORTH LOW PASS FILTER USING BILINEAR TRANSFORMATION
# Aim:

To design a digital Butterworth low pass filter using the bilinear transformation method in MATLAB satisfying the given constraints:

0.707≤∣H(ω)∣≤1.0;0≤ω≤0.2π

∣H(ω)∣≤0.08;0.4π≤ω≤π

Assume sampling period T=1second.

# APPARATUS REQUIRED :
MATLAB software
Computer system

Given Specifications

Passband edge frequency:

ω_p=0.2π

Stopband edge frequency:

ω_s=0.4π

Passband ripple:

A_p=-20〖log⁡〗_10 (0.707)=3" dB"

Stopband attenuation:

A_s=-20〖log⁡〗_10 (0.08)≈21.94" dB"

Sampling period:

T=1" second"

# THEORY :
The Butterworth filter is a maximally flat magnitude filter with no ripples in the passband and stopband.
The bilinear transformation converts an analog filter into a digital filter using the relation:

s=2/T  (1-z^(-1))/(1+z^(-1) )

Frequency pre-warping is done to compensate for frequency distortion introduced by bilinear transformation.
The steps involved are:

1)Prewarp digital frequencies to analog frequencies.  

2)Design analog Butterworth filter.
  
3)Convert analog filter into digital filter using bilinear transformation.
  
4)Plot magnitude and phase response.

# ALGORITHM :

1.	Specify passband and stopband edge frequencies.
2.	Convert digital frequencies to analog frequencies using pre-warping.
3.	Compute filter order and cutoff frequency using Butterworth approximation.
4.	Design analog Butterworth low pass filter.
5.	Convert analog filter into digital filter using bilinear transformation.
6.	Plot frequency response using freqz.
7.	Verify whether the filter satisfies the given constraints.

# MATLAB CODE :
~~~
clc;
clear;
close all;

T = 1; % Sampling period

wp = 0.2*pi;   % Passband frequency
ws = 0.4*pi;   % Stopband frequency

Ap = 3;        % Passband ripple (dB)
As = 21.94;    % Stopband attenuation (dB)

% Pre-warping
Wp = (2/T)*tan(wp/2);
Ws = (2/T)*tan(ws/2);

% Order and cutoff frequency
[N, Wn] = buttord(Wp, Ws, Ap, As, 's');

% Analog Butterworth filter
[b, a] = butter(N, Wn, 's');

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
title('Magnitude Response of Digital Butterworth LPF');

% Plot phase response
figure;
plot(w/pi, angle(H));
grid on;
xlabel('Normalized Frequency (\times\pi rad/sample)');
ylabel('Phase (radians)');
title('Phase Response of Digital Butterworth LPF');
~~~
# OUTPUT GRAPH :
<img width="714" height="495" alt="image" src="https://github.com/user-attachments/assets/43b7c2f1-6884-4c03-8e10-4fc96e7f679c" />
<img width="722" height="488" alt="image" src="https://github.com/user-attachments/assets/4d415a73-c5c0-4f44-a5eb-f80460a496c7" />

# RESULT:
A digital Butterworth low pass filter satisfying the given constraints was successfully designed using the bilinear transformation method and its frequency response was verified using MATLAB.



