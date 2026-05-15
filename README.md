# Pulse-Code-Modulation
# Aim
Write a simple Python program for the modulation and demodulation of PCM, and DM.
# Tools required
# Program
```
import numpy as np
import matplotlib.pyplot as plt

# ---------------- PARAMETERS ----------------
fs = 1000          # sampling frequency
Tb = 1             # bit duration
fc = 5             # carrier frequency
data = [1,0,1,1,0,1]

t = np.arange(0, Tb, 1/fs)

# ---------------- MESSAGE ----------------
message = np.repeat(data, len(t))
time = np.arange(len(message)) / fs

# ---------------- CARRIER ----------------
carrier = np.sin(2*np.pi*fc*time)

# ---------------- PSK MODULATION ----------------
# 1 -> +1 , 0 -> -1
polar_data = 2*message - 1
psk = polar_data * carrier

# ---------------- DEMODULATION ----------------
demod = psk * carrier
reconstructed = (demod > 0).astype(int)

# ---------------- PLOTS ----------------
plt.figure(figsize=(12,8))

plt.subplot(4,1,1)
plt.plot(time, message)
plt.title("Message Signal")
plt.ylim(-0.5,1.5)
plt.grid()

plt.subplot(4,1,2)
plt.plot(time, carrier)
plt.title("Carrier Signal")
plt.grid()

plt.subplot(4,1,3)
plt.plot(time, psk)
plt.title("PSK Modulated Signal")
plt.grid()

plt.subplot(4,1,4)
plt.plot(time, reconstructed)
plt.title("Demodulated Signal")
plt.ylim(-0.5,1.5)
plt.grid()

plt.tight_layout()
plt.show()


```
# Output Waveform
```
<img width="1189" height="990" alt="download (2)" src="https://github.com/user-attachments/assets/54986ea9-d6b6-4e37-a0d0-9a48d794d974" />

```
# Results
```
Thus the modulation and demodulation of PCM, and DM is Verified
```
