## 1. 数组倒序遍历

```python
# 方法一
for num in nums[::-1]      //简写省略n-1
for num in nums[n-1::-1]   

# 方法二
for i in range(len(nums)-1, -1, -1):

# 方法三
for num in reversed(nums):
```

## 2. 随机种子

 seed( ) 用于指定随机数生成时所用算法开始的整数值，如果使用相同的seed( )值，则每次生成的随即数都相同，如果不设置这个值，则系统根据时间来自己选择这个值，此时每次生成的随机数因时间差异而不同。 

```
np.random.seed()
```

## 3. numpy.reshape(a, b)

**作用**：将数组以 转换为a行b列的形式显示。

**特殊用法**：mat (or array).reshape(c, -1);  必须是矩阵格式或者数组格式，才能使用 .reshape(c, -1) 函数， 表示将此矩阵或者数组重组，以 c行d列的形式表示（-1的作用就在此，自动计算d：d=数组或者矩阵里面所有的元素个数/c, d必须是整数，不然报错）（reshape(-1, e)即列数固定，行数需要计算）：

## 4. numpy.squeeze(a,axis = None) 

> 1）a表示输入的数组；
> 2）axis用于指定需要删除的维度，但是指定的维度必须为单维度，否则将会报错；
> 3）axis的取值可为None 或 int 或 tuple of ints, 可选。若axis为空，则删除所有单维度的条目；
> 4）返回值：数组
> 5) 不会修改原数组；

 **作用**：从数组的形状中删除单维度条目，即把shape中为1的维度去掉 。

场景：在机器学习和深度学习中，通常算法的结果是可以表示向量的数组（即包含两对或以上的方括号形式[[]]），如果直接利用这个数组进行画图可能显示界面为空。我们可以利用squeeze（）函数将表示向量的数组转换为秩为1的数组，这样利用matplotlib库函数画图时，就可以正常的显示结果了。

## 5. print的几种用法

#### 用法一

```python
num = 1000
print("The number is: " + str(num) + "!")

>>> The number is 1000!
```

#### 用法二

```python
num = 1000
print("The number is %d !" % num)

>>> The number is 1000 !
```

#### 用法三

```python
# 方法三可用于数组的输出
accuacy = 90.456
iteration = 100
print("Accuacy for {} iteraitons is {} %" .format(iteration, accuacy))

>>> Accuacy for 100 iterations is 90.456 %
```

## 6. lambda用法

```
lambda arguments1, arguments2: expression

# 单个参数
lambda x: x**2

# 多个参数
lambda x, y, z : x+y+z
```

和python的排序函数结合使用

```
# 根据等式的大小对序列进行排序
points.sort(key=lambda x: x**2)
```

## 7. 二维数组遍历

#### 方式一：获取列表维度索引

```python
list2d = [[1,2,3],[4,5,6]]
sum = 0
for i in range(len(list2d)):
    for j in range(len(list2d[0])):
        sum += list2d[i][j]
print(sum)
```

评价：这种方式不好， 利用行列下标索引方式,则必须要求，每行的列数相同，容易出现数组索引的报错问题。

例如：

```python
list2d = [[1,2,3],[4,5]]
sum = 0
for i in list2d:
    for j in i:
        sum += j
print(sum)
```

出现报错： 因为得到列数为3，在第二行时就会超出索引。

```python
IndexError: list index out of range
```

#### 方式二：利用列表句柄

```python
list2d = [[1,2,3],[4,5]]
sum = 0
for i in list2d:
    for j in i:
        sum += j
print(sum)
```



