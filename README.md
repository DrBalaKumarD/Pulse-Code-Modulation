# Pulse-Code-Modulation
Aim:
To implement Pulse Code Modulation (PCM) for encoding and decoding a sinusoidal signal using quantization and to observe the output waveforms.


Tools/Software Required:

 1. Python Software

-> Numpy Library

-> Matplotlib Library

-> Scipy Library (for signal processing


Program:

import numpy as np

import matplotlib.pyplot as plt

def pcm_encode(signal, quantization_levels):
   
    min_val, max_val = np.min(signal), np.max(signal)
    
    quantized_signal = np.round((signal - min_val) / (max_val - min_val) * (quantization_levels - 1))
    
    return quantized_signal.astype(int)

def pcm_decode(encoded_signal, quantization_levels, min_val, max_val):
    
    decoded_signal = encoded_signal / (quantization_levels - 1) * (max_val - min_val) + min_val
   
    return decoded_signal

fs = 1000  # Sampling frequency

t = np.linspace(0, 1, fs)

original_signal = 0.5 * np.sin(2 * np.pi * 5 * t)  # 5 Hz sine wave

quantization_levels = 16

encoded_signal = pcm_encode(original_signal, quantization_levels)

decoded_signal = pcm_decode(encoded_signal, quantization_levels, np.min(original_signal), np.max(original_signal))

plt.figure(figsize=(12, 8))

plt.subplot(3, 1, 1)

plt.plot(t, original_signal, label='Original Signal')

plt.title('Original Signal')

plt.grid(True)

plt.subplot(3, 1, 2)

plt.step(t, encoded_signal, label='PCM Modulated Signal', color='r')

plt.title('PCM Modulated Signal')

plt.grid(True)

plt.subplot(3, 1, 3)

plt.plot(t, decoded_signal, label='Demodulated Signal', color='g')

plt.title('PCM Demodulated Signal')

plt.grid(True)

plt.tight_layout()

plt.show()

Output Waveform:

<img width="871" alt="image" src="https://github.com/user-attachments/assets/d78349ec-4e25-45a8-8e2e-f2b90004c576" />
<img width="882" alt="image" src="https://github.com/user-attachments/assets/12550ba4-fd9a-4a8a-acb0-660c611a4e20" />
<img width="873" alt="image" src="https://github.com/user-attachments/assets/8f0bc45f-b120-404c-9950-5c1f58173502" />

Results:

The PCM encoding process successfully quantized the original sine wave into 16 levels.

The demodulated signal closely resembled the original signal with minor quantization noise.

The output waveforms validated the functioning of PCM in digital communication systems.
