

```python
from __future__ import print_function
import numpy as np
import math
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D

import warnings
warnings.filterwarnings('ignore')
```


```python
def func1(t, der = False):
    if (der):
        return (-np.sin(t), np.cos(t))
    return (np.cos(t), np.sin(t))

def func2(t, der = False):
    if (der):
        return (np.cos(t), -np.sin(t))
    return (np.sin(t), np.cos(t))

def func3(t, der = False):
    if (der):
        return ((np.cos(t) - t * np.sin(t)), (np.sin(t) + t * np.cos(t)))
    return (t*np.cos(t), t*np.sin(t))

def func4(t, der = False):
    if (der):
        return (1/(2 * np.sqrt(1 - t)), -1/(2 * np.sqrt(t)))
    return (np.sqrt(1 - t), np.sqrt(t))
```


```python
def draw(func, data_t):
    fig = plt.figure(figsize = (12,12))
    ax = fig.add_subplot(111, projection='3d')
    ax.set_zlabel('T')
    ax.set_ylabel('Y')
    ax.set_xlabel('X')

    arrows_t = np.linspace(min(data_t), max(data_t), 5)
    ts = [arrows_t[1], arrows_t[2], arrows_t[3]]
    
    data_x = []
    data_y = []

    for t in data_t:
        x, y = func(t)
        data_x.append(x)
        data_y.append(y)
    
    ax.plot(data_x, data_y, data_t, zdir = 'z', color = 'blue',  linestyle = '-', label = "Graph")
    ax.plot(data_x, data_y, color = 'green', label = "path")
    
    colors = ['red', 'black', 'yellow']
    for t in ts:
        x, y = func(t)
        dx, dy = func(t, True)
        data_x = [x, x+dx]
        data_y = [y, y + dy]
        ax.plot(data_x, data_y, color = colors[ts.index(t)], label = "$\phi(t)'$, " + "t = " + str(t))
    plt.legend()
    plt.show()
```


```python
data_t1 = np.linspace(0, 2 * np.pi, 10000)

draw(func1, data_t1)
```


![png](output_3_0.png)



```python
data_t2 = np.linspace(0, 2 * np.pi, 10000)

draw(func2, data_t2)
```


![png](output_4_0.png)



```python
data_t3 = np.linspace(0, 100, 100000)

draw(func3, data_t3)
```


![png](output_5_0.png)



```python
data_t4 = np.linspace(0, 1, 10000)

draw(func4, data_t4)
```


![png](output_6_0.png)

