# Power Spectral Analysis of EEG Signal
# AIM :

To perform spectral analysis of an EEG signal using FFT in MATLAB.

# THEORY :

EEG signals contain multiple frequency components that correspond to different brain activities. Spectral analysis is a technique used to identify the distribution of signal power across different frequency components.
The Fast Fourier Transform (FFT) is an efficient algorithm used to compute the Discrete Fourier Transform (DFT). It converts the signal from the time domain into the frequency domain, allowing us to observe the dominant frequencies present in the EEG signal.
The mathematical expression for the Discrete Fourier Transform is:

X(k)=∑_(n=0)^(N-1)▒〖x(n)〗 e^(-j2πkn/N)

where:
x(n)= input signal
X(k)= frequency spectrum
N= number of samples
Using FFT, the computational complexity is reduced from N² operations to N log₂ N operations, making it suitable for real-time biomedical signal analysis.
Spectral analysis helps in identifying EEG rhythms such as alpha and beta waves, which are important in neurological studies, sleep analysis, and brain-computer interface systems.

# ALGORITHM :
1)Load EEG signal data.
2)Define the sampling frequency.
3)Apply FFT to convert the signal to the frequency domain.    
4)Compute magnitude spectrum.
5) Plot the power spectrum.
6) Identify dominant frequency components.

# MATLAB CODE :
```
clc;
clear;
close all;

load eegdata.mat

fs = 256;
N = length(eeg);

X = fft(eeg);
f = (0:N-1)*(fs/N);

plot(f,abs(X));
xlabel('Frequency (Hz)');
ylabel('Magnitude');
title('EEG Frequency Spectrum');
grid on;
```

# OUTPUT GRAPH :

<img width="1486" height="1017" alt="image" src="https://github.com/user-attachments/assets/bfacc324-0fdd-413b-ab3c-963fc48f950a" />


# RESULT :
The EEG signal spectrum was successfully obtained using FFT and frequency components were analyzed.

