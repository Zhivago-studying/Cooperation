# 绘图库matplotlib
## 1.简单绘图
```python
import matplotlib.pyplot as plt
import numpy as np
import math
### 正弦曲线
x = np.linspace(0, 2 * math.pi, 100)
y = np.sin(x)
plt.xlabel("angle")
plt.ylabel("sin")
plt.title("sin wave")
plt.plot(x, y)
plt.show()
### 条形图
x = np.arange(5)
y = [23,56,23,48,55]
plt.bar(x, y)
plt.show()
### 直方图
x = np.random.randn(1000)
plt.hist(x, bins=30) # bins=30表示将x分成30个区间，如果传了列表bin = [0,25,50,75,100]表示以这个列表为区间分割
plt.show()
plt.save.fig("./fig1") # 保存图片
```
## 先学这几根鸡毛吧，其他的你去看那个梗直哥