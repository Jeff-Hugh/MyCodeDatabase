# Calculation of Power Spectral Density (PSD)

**a is the signal**

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import signal

# Read data from file
# AllData = pd.read_csv("forceCoeffs.dat", delimiter='\s+', header=None, names=["Time", "Cm", "Cd", "Cl", "Cl_f", "Cl_r"], index_col=None, skiprows=10)

a = np.array([1.529215e+00,1.553725e+00,1.547487e+00,1.516702e+00,1.486448e+00,1.481946e+00,1.507633e+00,1.546760e+00,
              1.575737e+00,1.577126e+00,1.548575e+00,1.507958e+00,1.484047e+00,1.493184e+00,1.527433e+00,1.564181e+00,
              1.581555e+00,1.567912e+00,1.530069e+00,1.493585e+00,1.484153e+00,1.507060e+00,1.545521e+00,1.575737e+00,
              1.579266e+00,1.552315e+00,1.511231e+00,1.484970e+00,1.491336e+00,1.524236e+00,1.561839e+00,1.581318e+00,
              1.570134e+00,1.533491e+00,1.495693e+00,1.483645e+00,1.504286e+00,1.542420e+00,1.574149e+00,1.580149e+00,
              1.555373e+00,1.514488e+00,1.485952e+00,1.489589e+00,1.521025e+00,1.559168e+00,1.580765e+00,1.572175e+00,
              1.536953e+00,1.498180e+00,1.483331e+00,1.501721e+00,1.539257e+00,1.572236e+00,1.580842e+00,1.558300e+00,
              1.517679e+00,1.487217e+00,1.488045e+00,1.517899e+00,1.556390e+00,1.580044e+00,1.574077e+00,1.540435e+00,
              1.500747e+00,1.483260e+00,1.499183e+00,1.535901e+00])

freqs, psd = signal.welch(a)
plt.figure(figsize=(5, 4))
#plt.semilogx(freqs, psd)
plt.plot(freqs, psd)
plt.title('PSD: power spectral density')
plt.xlabel('Frequency')
plt.ylabel('Power')
plt.show()
print(freqs)
print(psd)
```