## value_counts()

pandas中value_counts()可以返回对Series中每个值进行计数，并且默认按照降序排序

如果想要做升序排列，参数ascending=True

如果想要得出计数占比，参数normalize=True

空值默认是剔除掉的

# np.argsort()

numpy中的函数，用来返回一个数组从小到大排好序之后各元素对应的位置索引

```python
c = np.array([3,2,5,1,7,2,9,4])
d = np.argsort(c)
[out]：array([3, 1, 5, 0, 7, 2, 4, 6], dtype=int64)
```

# fillna()





# _的含义

单下划线作为“一次性”变量名称，表示功能结果的一部分被故意忽略，表示某个变量是临时的或者无关紧要的

```python
car = ('red', 'auto', 12, 3812.4)
color, _, _, mileage = car
该组代码中我不关心中间两个变量的值，所以用_作为占位符，只提取出来一部分变量
color->'red'
mileage->3812.4
```

在解释器中也可以用以访问最近一个表法式的结果

```python
20 + 3
 _->23
```

# enumerate()

函数用于将一个可遍历的数据对象组合为一个索引序列，同时列出数据和数据下标

```python
seq = ['one', 'two', 'three']
for i, element in enumerate(seq):
    print(i, element)
[out]:
0 one
1 two
2 three   
```





# df.columns.values

df.values获取的是df中的数据

```python
df=pd.DataFrame({"A":[1,2,3,4],"B":[5,6,7,8],"C":[1,1,1,1]})
df.values
[out]array([[1, 5, 1],
       [2, 6, 1],
       [3, 7, 1],
       [4, 8, 1]], dtype=int64)
df.columns.values
[out]array(['A', 'B', 'C'], dtype=object)
df.A.values
[out]array([1, 2, 3, 4], dtype=int64)
```



# np.unique()

np.unique()参数是一维数组或者列表，unique去除其中重复的元素并按元素从小到达排序返回一个列表

```python
A = [1,2,2,2,5,3,4,3]
np.unique(A)
[out] array([1, 2, 3, 4, 5])
B = (1,2,2,2,5,3,4,3)
np.unique(B)
[out] array([1, 2, 3, 4, 5])
```

np.unique(,return_index=True)返回排序列表，并返回新列表元素在旧列表中第一次出现的位置

```python
a,s = np.unique(A,return_index = True)
a->array([1, 2, 3, 4, 5])
s->array([0, 1, 5, 6, 4], dtype=int64)
```

np.unique(df.columns.values,return_counts=True)返回排序列表，并返回排序列表中每个元素在原始列表中出现的次数

```python
b=np.random.randint(0,5, size=(10))
b->array([3, 0, 4, 2, 0, 4, 3, 4, 2, 3])
np.unique(b, return_counts=True)
[Out]:(array([0, 2, 3, 4]), array([2, 2, 3, 3], dtype=int64))
```



# np.log()

log()两个底数10和e的log计算

np.log10()  以10 为底

np.log() 以e为底

* log函数是单调增函数，取对数后不会改变数据的相对关系
* 缩小数据的绝对值，计算方便
* 取对数可以将乘法计算转换为加法计算
* 取对数的时候确保数据集中没有负数

# tolist()

将数组array或者矩阵matrix等转为列表list形式

```python
a1 = [[1,2,3],[4,5,6]]
a2 = array(a1)
array([[1, 2, 3],
       [4, 5, 6]])
a3 = mat(a1)
matrix([[1, 2, 3],
        [4, 5, 6]])
a2.tolist()
a3.tolist()
```

# np.bincount(Series,minlength)

将Series的值范围作为索引值，统计Series的每个索引值出现的次数

```python
x = np.array([0,1,1,3,2,1,7])#bin=8,索引值为0-7
np.bincount(x)
[out]array([1, 3, 1, 1, 0, 0, 0, 1], dtype=int64)
```

如果指定参数minlength,那么输出数组中bin的数量至少为指定的数（bin的数量小，就是指定的数；bin的数量大则保留bin）

```python
x = np.array([3,2,1,3,1])
np.bincount(x,minlength=7)
[out]:array([0, 2, 1, 2, 0, 0, 0], dtype=int64)
np.bincount(x,minlength=1)
[out]:array([0, 2, 1, 2], dtype=int64)
```



# dict()

* dict()用于创建字典

* 和zip联用表示映射函数方式来构造字典

```python
dict(zip(*(['one','two','three'],[1,2,3])))
#dict(zip(['one', 'two', 'three'], [1, 2, 3]))
[out]{'one': 1, 'two': 2, 'three': 3}
```

* 用可迭代对象构造字典

```pyhton
dict([('one', 1), ('two', 2), ('three', 3)])
[out]{'one': 1, 'two': 2, 'three': 3}
```



# zip()

* zip()作用将可迭代对象中的元素打包成一个个元组，返回这些元祖组成的列表

* 如果各个迭代器的元素个数不一致，返回列表长度和最短的对象相同
* zip()于压缩，zip(*)相当于解压
* zip之后的内容直接输出是一个zip对象，必须经过list才能显示出来

```python
a = [1,2,3]
b = [4,5,6]
zipped = zip(a,b)
list(zipped)
[out]:[(1, 4), (2, 5), (3, 6)]
list(zip(*zipped))
[out]:[(1, 2, 3), (4, 5, 6)]
```

sum() ---- df.isnull().sum()

drop(df.columns,axis=1) axis分别表示

pd.concat()

datetime.datetime()

# np.where()

np.where(condition,x,y)表示如果满足条件就返回x值，不满足条件就返回y

```pyhton
x = np.random.randn(4,4)
x:array([[ 0.11723132,  1.31485786, -0.13477235, -0.24620394],
       [ 2.20146692, -2.14839107, -0.65261514, -0.37013939],
       [ 1.58552084,  1.55633968,  0.43187894,  0.54793133],
       [ 2.25123579,  0.84567756,  0.60481034,  1.99548516]])
np.where(x>0,2,-2)
array([[ 2,  2, -2, -2],
       [ 2, -2, -2, -2],
       [ 2,  2,  2,  2],
       [ 2,  2,  2,  2]])
```

# np.logical_and(<200,>1900)

逻辑与

```python
x  = np.arange(5)
x:array([0, 1, 2, 3, 4])
np.logical_and(x>1,x<4)
[out]:array([False, False,  True,  True, False])
```





如果要清除环境中的某个变量，用del 变量名

清除环境中所有的变量 reset

变量命名的时候不要用python自带的方法，否则容易引起'int' object is not callable错误

np求平均值的时候如何忽略nan np.mean()->np.nanmean(),同样的np.nanmax()、np.nanmin()

将DataFrame存储到csv文件中用to_csv()，df.to_csv(filename,index=False)

# df.rename()

对DataFrame的列名重新命名用rename()   df.rename(columns={'A':'a'},inplace=True)

其中，inplace的意思是不使用复制的方式在原来的df上直接修改，如果是False，需要复制给另一个dataframe，原来的df不变

使用list创建dataframe示例：

```python
a = [['2', '1.2', '4.2'], ['0', '10', '0.3'], ['1', '5', '0']]

df = pd.DataFrame(a,columns=['one','two','three'])
```

|      |  one |  two | three |
| ---: | ---: | ---: | ----: |
|    0 |    2 |  1.2 |   4.2 |
|    1 |    0 |   10 |   0.3 |
|    2 |    1 |    5 |     0 |

单独每列数据使用fillna()和全部数据使用fillna()的区别

# type()、dtype、astype()区别

* type()获取数据类型 list和np.array都有

* dtype 获取数据元素类型  只有np.array有，arr.dtype

* astype 修改数据类型 只有np.array有，arr.astype(np.int)



读取csv文件的时候想读取一部分数据应该怎么读

写入文件的时候一行一行数据读入和一行一行数据写入应该怎么操作

对于h5文件怎么一部分一部分读入



# df.loc[]和df.iloc[]

* iloc利用index的具体位置获取想要的行或者列，只能是整数型参数

* ioc利用index的名称获取想要的行或者列

# 计算两个日期之间相差的天数

```python
import datetime
d1 = datetime.datetime(2005, 2, 16)
d2 = datetime.datetime(2004, 12, 31)
(d1 - d2).days
[out]47
```

timestamp类型和datetime类型的区别

将数据文件保存在不同的文件夹，使用python语句移动文件夹的位置



DataFrame、Series才有value_counts函数 







保存jypeter环境下的变量以及恢复当前的环境

