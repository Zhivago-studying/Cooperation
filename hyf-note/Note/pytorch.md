# 就是pytorch咯，跟那个numpy一毛一样

## 属性
```python
import torch
x.shape  # 各轴长度
x.numel()  # 元素个数,即size
```

## 创建
```python
x = torch.tensor([[1, 2, 4],
                  [3, 5, 6]])   #自己捏
x = torch.arange(12).reshape(3, 4)  #前12个，再转型
x = torch.randn(2, 3, 4)  # 随机数,标准正态分布
x = torch.zeros(2, 3, 4)  # 一坨0
```

## 运算
```python
# 加减乘除，** 是幂运算，都是按位运算
torch.exp(x) # e指数
```

## 拼接
```python
torch.cat((x, y), dim=0) #指定按那个轴拼接
```

## 比较
返回bool矩阵

## 统计
```python
x.sum() # 求和，指定参数可以指定轴，实现降维
x.mean() # 求平均,指定参数可以指定轴，实现降维
```

## 索引
左闭右开
```python
x[0:2, :]  # 第一行和第二行，所有列
```

## 节省内存
```python
Z[:] = X + Y # 赋值后，Z的地址不变
X += Y # 赋值后，X的地址不变
X = X + Y # 赋值后，X的地址改变
```

## 线性代数
```python
len(x) #访问向量x的长度
x.T #转置
torch.dot(x, y) #向量内积
torch.mv(X, y) #矩阵与向量相乘
torch.mm(X, Y) #矩阵乘法
```

## 范数(norm)
```python
'''三个性质
1.  f(ax) = |a|f(x) #绝对值缩放
2.  f(x+y) <= f(x)+f(y) #三角不等式
3.  f(x) >= 0 #非负性
'''
torch.norm(x) # L2范数  ||u||
torch.norm(x, p=1) # L1范数  ||u||_1
torch.norm(A) # frobenius范数  ||A||_F,是矩阵类似于向量L2范数的范数
```

## 自动微分
```python
import torch
x = torch.tensor([4.0], requires_grad=True) 
#或者分开写x = torch.tensor([4.0]) x.requires_grad_(True)
y = 2 * torch.dot(x, x)
y.backward()    #反向传播
x.grad          #梯度

x.grad.zero_()  #梯度清零,因为会累计
y = x * x       # y 不是标量，而是向量
y.sum().backward() #等价于y.backward(torch.ones(len(x)))
x.grad          

x.grad.zero_()
y = x * x
u = y.detach()  #复制一个y，把u 视为常量
z = u * x

z.sum().backward() 


