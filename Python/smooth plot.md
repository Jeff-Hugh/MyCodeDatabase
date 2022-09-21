# make the curve more smooth

```python
import matplotlib.pyplot as plt
from scipy.interpolate import make_interp_spline, BSpline
import numpy as np

NPR = np.array([10,20,30,40,45,50,55,60,])
F_exp = np.array([0.993182,0.864773,0.905682,0.867045,0.857955,0.854545,0.842045,0.882955,])
F_cal = np.array([0.944795446,0.977510351,0.985260175,0.984477896,0.98292701,0.981420127,0.97936905,0.978118417])
flow_exp = np.array([0.8109,0.995,0.99,1.076,1.0703,1.077,1.125,1.054])
flow_cal = np.array([0.992393525,0.992850293,0.992994879,0.993174117,0.993123412,0.99313242,0.993120824,0.993095326])

plt.rcParams['axes.labelsize'] = 24
plt.rcParams['xtick.labelsize'] = 24
plt.rcParams['ytick.labelsize'] = 24
plt.rcParams['lines.markersize'] = 12
plt.rcParams['figure.figsize'] = 13, 10
plt.rcParams['legend.fontsize'] = 24

NPR_new = np.linspace(NPR.min(), NPR.max(), 100)
spl = make_interp_spline(NPR, F_exp, k=3)
F_exp_s = spl(NPR_new)
spl = make_interp_spline(NPR, F_cal, k=3)
F_cal_s = spl(NPR_new)

f1 = plt.figure(1)
plt.plot(NPR_new, F_exp_s, label='Experimental', linestyle='-', color='r', linewidth = 3)
plt.plot(NPR_new, F_cal_s, label='Calculated', linestyle='-', color='b', linewidth = 3)
plt.plot(NPR, F_exp, color='r', marker='*', linestyle='None')
plt.plot(NPR, F_cal, color='b', marker='^', linestyle='None')
plt.ylabel('Thrust coefficient')
plt.xlabel('NPR')
plt.legend(loc='best')
f1.savefig("Thrust.png", dpi=300)

```