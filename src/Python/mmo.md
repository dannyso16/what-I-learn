# memo

## 3d plot as subplot

![../../_images/sphx_glr_subplot3d_001.png](.\mmo.assets\sphx_glr_subplot3d_001.png)

こういうのがしたい

```python
ax = fig.add_subplot(1, 2, 1, projection='3d')
```



## 一つの画像に複数のプロット

[ここ](http://ailaby.com/matplotlib_fig/)

```python
x = np.linspace(-3, 3, 20)
y1 = x
y2 = x ** 2
 
# figure は 1 つ
plt.figure(figsize=(3, 4))
 
plt.subplot(2,1,1)
plt.plot(x, y1)
 
plt.subplot(2,1,2)
plt.plot(x, y2)
 
plt.show()
```

![plot_win_1](.\mmo.assets\plot_win_1.png)