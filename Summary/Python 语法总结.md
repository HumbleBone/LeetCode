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

## 8. 数组元素删除

#### 方法一：del

```
li = [1, 2, 3, 4]
del li[3]
print(li)
# Output [1, 2, 3]
```

#### 方法二：pop

```
li = [1, 2, 3, 4]
li.pop(2)
print(li)
# Output [1, 2, 4]
```

#### 方法三：切片删除元素

```
li = [1, 2, 3, 4]
li = li[:2] + li[3:]
print(li)
# Output [1, 2, 4]
```

#### 方法四：remove删除指定元素

```
li = [1, 2, 3, 4]
li.remove(3)
print(li)
# Output [1, 2, 4]
```

 注：remove方法删除指定值的元素，与其他方法不同。 

## 9. 数组元素增加

#### 方法一：append

**append() 追加单个元素到List的尾部**，只接受一个参数，参数可以是任何数据类型，被追加的元素在List中保持着原结构类型。

此元素如果是一个list，那么这个list将作为一个整体进行追加，注意append()和extend()的区别。

```
>>> list1=['a','b']
>>> list1.append('c')
>>> list1
['a', 'b', 'c']
```

#### 方法二：extend

 **extend() 将一个列表中每个元素分别添加到另一个列表中**，只接受一个参数；extend()相当于是将list B 连接到list A上。 

```
>>> list1
['a', 'b', 'c']
>>> list1.extend('d')
>>> list1
['a', 'b', 'c', 'd']
```

#### 方法三：insert

 **insert() 将一个元素插入到列表中，但其参数有两个（如insert(1,”g”)），**第一个参数是索引点，即插入的位置，第二个参数是插入的元素。 

```
>>> list1
['a', 'b', 'c', 'd']
>>> list1.insert(1,'x')
>>> list1
['a', 'x', 'b', 'c', 'd']
```

#### 方法四：+号相加

 **+ 加号，将两个list相加，会返回到一个新的list对象，注意与前三种的区别。**前面三种方法（append, extend, insert）可对列表增加元素的操作，他们没有返回值，是直接修改了原数据对象。 注意：将两个list相加，需要创建新的list对象，从而需要消耗额外的内存，特别是当list较大时，尽量不要使用“+”来添加list，而应该尽可能使用List的append()方法。 

```
>>> list1
['a', 'x', 'b', 'c', 'd']
>>> list2=['y','z']
>>> list3=list1+list2
>>> list3
['a', 'x', 'b', 'c', 'd', 'y', 'z']
```

## 10. 返回数组中指定元素的索引

使用 `index()` 函数，例如返回数组中最小元素的索引：

```
n = [20, 15, 27, 30]
n.index(min(n))
>>> 1
```

