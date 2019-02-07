# Slope field

---

```python
from __future__ import print_function
import numpy as np
import math
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D

import warnings
warnings.filterwarnings('ignore')   # silent mode
```

---

```python
def func(t, x, der = True, x0 = None):
    if (der):
        return f(t,x)         # from the task
    if (x0 != None):
        if (x0 > 0):
            return true_f(x)  # your solution
        else:
            return -true_f(x) #
```
---

```python
dots = np.linspace(-5, 5, 40)

eps = 0.03
 
plt.figure(figsize=(12,12))
    
plt.title("Task №", {'fontsize' : 15, 'verticalalignment': 'baseline'})
 
for x in dots:
    for t in dots:
        tg = func(t, x)
        delta = np.sqrt(eps / (1 + tg**2)) / 2
        data_t = [t - delta, t + delta]
        data_x = [x - delta * tg, x + delta * tg]
        plt.plot(data_t, data_x, color = 'green')
    
colors = ['red', 'black']
x0 = [2, -1]
        
for x in x0:
    data_t = np.linspace(-5, 5, 10000)
    data_x = []
            
    for t in data_t:
        data_x.append(func(t, t, der = False, x0 = x))
            
    plt.plot(data_t, data_x, color = colors[x0.index(x)], label = 'x0 = ' + str(x))
            
            
            
plt.grid(True)
plt.legend(prop={'size': 15})
plt.show()
```
