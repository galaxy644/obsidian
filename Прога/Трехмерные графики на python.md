import numpy as np  
import matplotlib.pyplot as plt  
  
def f(x, y):  
return x ** 2 + y ** 2  
  
x = np.linspace(-100, 100, 50)  
y = np.linspace(-100, 100, 50)  
x, y = np.meshgrid(x, y)  
z = f(x, y)  
  
fig = plt.figure(figsize=(10,10))  
ax = plt.axes(projection='3d')  
ax.plot_surface(x,y,z)  
plt.show()