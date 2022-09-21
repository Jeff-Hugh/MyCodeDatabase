# matplotlib code commonly used

```python
import matplotlib.pyplot as plt

plt.rcParams['axes.labelsize'] = 24
plt.rcParams['xtick.labelsize'] = 24
plt.rcParams['ytick.labelsize'] = 24
plt.rcParams['lines.markersize'] = 12
plt.rcParams['figure.figsize'] = 13, 10
plt.rcParams['legend.fontsize'] = 24

f1 = plt.figure(1)
plt.plot(NPR, F_exp, label='Experimental', linestyle='-', color='r', linewidth = 3, marker='*')
plt.plot(NPR, F_cal, label='Calculation', linestyle='-', color='b', linewidth = 3, marker='^')
plt.ylabel('Thrust coefficience')
plt.xlabel('NPR')
plt.legend(loc='best')
f1.savefig("Thrust.png", dpi=300)

f2 = plt.figure(2)
plt.plot(NPR, flow_exp, label='Experimental', linestyle='-', color='r', linewidth=3, marker='*')
plt.plot(NPR, flow_cal, label='Calculation', linestyle='-', color='b', linewidth=3, marker='^')
plt.ylabel('Flow coefficience')
plt.xlabel('NPR')
plt.xlim([0, 1])
plt.legend(loc='best')
f2.savefig("Flow.png", dpi=300)

# plot3D
f_xyz = plt.figure(figsize=(15,10))
ax = f_xyz.gca(projection='3d')
plt.rcParams['axes.labelsize'] = 24
plt.rcParams['xtick.labelsize'] = 20
plt.rcParams['ytick.labelsize'] = 20
plt.rcParams['lines.markersize'] = 12
plt.rcParams['figure.figsize'] = 13, 10
plt.rcParams['legend.fontsize'] = 24

a_start = 0.1
a_end = 1.0
da = 0.05
for a in np.arange(a_start, a_end, da):
    t, x, y, z = func(a)
    ax.plot3D(x, y, z, linestyle='-', color=(1-a/a_end,0.1,a/a_end), linewidth = 3)

ax.view_init(30, 120)
plt.xlim([0,1])
plt.ylim([0,1])
ax.set_zlim(0,1)
plt.xlabel('x')
plt.ylabel('y')
ax.set_zlabel('z')
plt.show()
f_xyz.savefig("E1_xyz.png", dpi=600)
```