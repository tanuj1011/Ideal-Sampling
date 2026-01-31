# Ideal, Natural, & Flat-top -Sampling
# Aim
Write a simple Python program for the construction and reconstruction of ideal, natural, and flattop sampling.
# Tools required
#colab
# Program

### IDEAL SAMPLING 
```   
import numpy as np
import matplotlib.pyplot as plt
fs = 100   
f = 5       # signal frequency
t = np.arange(0, 1, 1/fs)
x = np.sin(2*np.pi*f*t)
plt.plot(t, x)
plt.title("Continuous Signal")
plt.xlabel("Time")
plt.ylabel("Amplitude")
plt.grid()
plt.show()
plt.stem(t, x)
plt.title("Ideal Sampling")
plt.xlabel("Time")
plt.ylabel("Amplitude")
plt.grid()
plt.show()
```
### NATURAL SAMPLING 
```
import numpy as np
import matplotlib.pyplot as plt
t = np.linspace(0, 1, 1000)
x = np.sin(2*np.pi*5*t)
p = ((t*50) % 1 < 0.5)   
xn = x * p                
t_rec = np.linspace(0, 1, 1000)
x_rec = np.interp(t_rec, t[p], x[p])
plt.plot(t, x); plt.title("Message Signal"); plt.show()
plt.plot(t, p); plt.title("Pulse Train"); plt.show()
plt.plot(t, xn); plt.title("Natural Sampling"); plt.show()
plt.plot(t_rec, x_rec); plt.title("Reconstructed Signal"); plt.show()
```
### FLAT TOP SAMPLING
```
import numpy as np
import matplotlib.pyplot as plt
from scipy.signal import butter, filtfilt
t = np.linspace(0, 1, 1000)
f = 5
x = np.sin(2 * np.pi * f * t)
p = ((t * 50) % 1 < 0.5).astype(float)  
xn = x * p                              
fs = 1000           
cutoff = 10          
order = 4
b, a = butter(order, cutoff / (fs / 2), btype='low')
x_rec = filtfilt(b, a, xn)
plt.figure()
plt.plot(t, x)
plt.title("Message Signal")
plt.xlabel("Time")
plt.ylabel("Amplitude")
plt.grid()
plt.show()
plt.figure()
plt.plot(t, p)
plt.title("Pulse Train")
plt.xlabel("Time")
plt.ylabel("Amplitude")
plt.grid()
plt.show()
plt.figure()
plt.plot(t, xn)
plt.title("Natural Sampling")
plt.xlabel("Time")
plt.ylabel("Amplitude")
plt.grid()
plt.show()
plt.figure()
plt.plot(t, x_rec, label="Reconstructed Signal")
plt.plot(t, x, 'r--', label="Original Signal")
plt.title("Reconstructed Signal using Butterworth Filter")
plt.xlabel("Time")
plt.ylabel("Amplitude")
plt.legend()
plt.grid()
plt.show()
```
# Output Waveform

1.IDEAL SAMPLING

<img width="587" height="455" alt="image" src="https://github.com/user-attachments/assets/13e07a52-07b2-4536-a0e5-37c458898bcb" />
<img width="587" height="455" alt="image" src="https://github.com/user-attachments/assets/bda7ede3-8644-483b-801d-bf5e9c2006d9" />
<img width="587" height="455" alt="image" src="https://github.com/user-attachments/assets/54147eb8-b836-4d37-82c6-e6fc013a3239" />



2.NATURAL SAMPLING

<img width="568" height="435" alt="image" src="https://github.com/user-attachments/assets/76775a51-5a82-488e-b35b-c6c48d83a553" />
<img width="547" height="435" alt="image" src="https://github.com/user-attachments/assets/62a75963-3dd9-440c-a6ff-5bdf2616a2e1" />
<img width="568" height="435" alt="image" src="https://github.com/user-attachments/assets/47a03f87-1cc8-4594-b786-cbc28ea7fcfe" />
<img width="568" height="435" alt="image" src="https://github.com/user-attachments/assets/0eea162d-6c09-42e8-a0c4-8bc12ce917db" />

3.FLAT TOP SAMPLING

<img width="587" height="455" alt="image" src="https://github.com/user-attachments/assets/190e2e8c-4c49-4dca-a25b-e7d76babc4b8" />
<img width="587" height="455" alt="image" src="https://github.com/user-attachments/assets/d9bbcf14-98db-4291-b119-2b5cbf047e22" />
<img width="587" height="455" alt="image" src="https://github.com/user-attachments/assets/519e7e14-a946-41c0-9f03-f200261f46b0" />

# Results
Thus, the construction and reconstruction of Ideal, Natural, and Flat-top sampling were successfully implemented using Python, and the corresponding waveforms were obtained.
