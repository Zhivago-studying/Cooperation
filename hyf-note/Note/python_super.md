# python 进阶
1. **内置函数**    
   1.1 
   ```python
    abs(x)  # 返回x的绝对值
    pow(x, y) # 返回x的y次方
    sum(list) # 返回list的和
    v1, v2 = divmod(x, y) # 返回商和余数
    round(x) # 返回x的四舍五入值
    ```
    1.2 
    ```python
    min(x, y) 
    max(list)
    all(list) #只有list全为真，返回True
    any(list) #只要list中有一个为真，返回True
    ```
    1.3
    ```python
    int('0xff',base=16)
    int('0o77',base=8)
    int('0b1010',base=2) #转十进制
    bin(10) #转二进制
    oct(10) #转八进制
    hex(10) #转十六进制
    ```
    1.4
    ```python
    ord('a') #返回a的ASCII码
    chr(97) #ASCII码为97的字符


2. **生产随机数**
    ```python
    import random
    random.randint(1, 100) #生成1-100的随机整数
    random.uniform(0,1) #均匀分布
    random.gauss(1,5) #高斯分布,均值1,标准差5
