### Numpy入门100题-前50题

---

#### 2020/3/11 1 - 10题

1. np.itemsize——每一个元素的类型所占的位数

2. np.show_config——查看numpy的版本和配置

3. np.info(np.某个函数)——在命令行下查看numpy关于某个函数的文档

4. np.arange(n, m)——创建一个值从 n 到 m - 1 的数组

   np.arange(n)——创建一个值从 0 到 n - 1 的数组

   np.arange(n).reshape(x, y)——创建一个值从 0 到 n - 1 的 x * y 的矩阵

5. a = a[ :: -1]——将一个数组反转（第一个元素变成最后一个，以此类推）

6. a = a[ : -n]——从a[0]取到数组倒数第 n + 1 个元素

7. np.nonzero(a)——返回数组a中非0的索引（非零元素在数组中的位置）

---

#### 2020/3/12 11 - 20题

1. np.random.random((n, m, z))——随机生成一个 n * m * z 的矩阵

   np.random.randint(n, m, z)——随机生成[n, m]区间内的z个数形成矩阵

   np.random.uniform...(无符号数)

2. a.mean() / a.max() / a.min()——返回矩阵a的平均值/最大值/最小值

3. np.eye(n)——生成一个 n * n 的对角矩阵

4. a[n : m, x : y] = ？——对矩阵a的第 n 至 m 列，每列的第 x 至 y个元素赋值

5. np.pad(array, pad_width = n, mode='constant', constant_values = m)——该函数作用相当于把一个矩阵当作一个长方形，长宽都增加 2n 。若原矩阵为 a * b, 现在矩阵为 (a + 2n) * (b + 2n)，多的部分的填充值为 m

6. math.isnan(np.nan)——安全检测nan值(ps：nan(not a number)用于处理计算中错误的情况，比如：0 / 0 )

7. np.diag(array, k)——当矩阵array为一维时，返回一个对角线依次为该数组元素，其他元素均为0的矩阵；当矩阵为二维时，返回其对角线元素，当 k > 0 时，返回矩阵对角线右上方的平行线上的元素；当 k < 0 时，返回矩阵对角线左下方的平行线上的元素。

8. array[start: end: step]——选取矩阵array中的部分元素，从start行到end行，步长为step(start和end可以省略)

9. np.unravel_index(x, array.shape)——返回第x个元素在矩阵array中的索引

---

#### 2020/3/15 21 - 30题

1. np.tile(array, n)——将矩阵array沿x轴复制“到”n倍(单个向量变长)

   np.tile(array, (n, m))——将矩阵array沿x轴复制“到”m倍(单个向量变长)，沿y轴复制“到”n倍(向量数量增加)

   ps: tile函数后一个参数的变化引起矩阵维数的变化

2. np.std(array)——计算全局标准差

   np.std(array, axis = 0)——计算每一列的标准差

   np.std(array, axis = 1)——计算每一行的标准差

   array = (array - np.mean(array)) / (np.std(array))——计算矩阵的标准差 

3. np.dot(x, y) / x @ y ——矩阵相乘的两种形式

4. array[(array > 3) & (array <= 5)]——对矩阵中大于3且小于等于5的元素进行操作

5. np.sum(array, axis = 0)——按列求和

   np.sum(array, axis = 1)——按行求和

6. np.mat()——创建矩阵

7. / ——除号

   //——整除

8. np.abs(array)——矩阵中所有元素取绝对值

9. np.ceil(array)——返回大于等于每个元素的最小整数

10. np.copysign(array1, array2)——将array2中的元素符号依此赋给array1中的每个元素(两矩阵的shape应该相同)

    np.copysign(array1, num1)——将num1的符号赋给array1中的每个元素

11. np.intersect1d(array1, array2)——返回两个矩阵中的相同的值组成的矩阵(输入矩阵的格式不需要一致，可以任意)

---

#### 2020/3/18 31 - 40题

1. np.sqrt(-1)——报错

   np.emath.sqrt(-1)——emath自动域数学函数，扩展到复数，该式子结果是1j
   
2. np.datetime('today', 'D')——获取今天的日期，python日期接口

   np.arange('2020-02', '2020-03', dtype = 'datetime64[D]')——获取2020年2月的所有日期
   
3. np.add(array1, array2, out = array1)——将矩阵相加的结果赋给array1

   np.divide(array1, 2, out = array1)——矩阵中每个元素都除以2

   np.negative(array1, out = array1)——矩阵所有元素乘-1
   
   np.multiply(array1, array2)——矩阵对应元素相乘，输出与相乘矩阵的大小一致
  
   ps: 灵活运用可以达到避免复制的目的
  
4. 提取矩阵中所有元素的整数部分的5种方法

   z = np.random.uniform(0, 10, (10, 10))

   print(z - z % 1)——数学方法
   
   print(np.floor(z))——np.floor()返回不大于输入参数的最大整数
   
   print(np.ceil(z) - 1)——np.ceil()返回大于输入参数的最小整数
   
   print(z.astype(int))——np.astype()数据类型转换（将浮点数转换成整数时，小数部分会被截断）
   
   print(np.trunc(z))——np.trunc()返回输入参数的整数部分
   
5. np.around(array1, decimals=0, out=None)——返回输出参数四舍五入之后的值
                                            decimals参数的值对应四舍五入的小数位数，默认为0
                                            
6. yield——可记录数据的迭代对象，可以记录上一次函数运行的值，并且在下一个迭代中使用，减少内存消耗

7. array.sort(cmp = None)——比较的标准可以自己写函数来规定，默认是从小到大排列

8. np.linspace(start, stop, num, endpoint=True, retstep=False, dtype=None)——endpoint(True,包括stop;False,不包括stop), num(生成的样本数),

   retstep(True, step = (stop - start) / (num - 1);False, step随机)
   
---

#### 2020/3/24 41 - 50题（偷懒多天/(ㄒoㄒ)/~）

1. 判断两个array是否相等的方法

   np.allclose(array1, array2)——比较两个array是否每个元素都相等(在1e-05范围内)

   np.array_equal(array1, array2)——比较两个array是否相等
   
2. array.flags.writeable = False——锁定array，使得array不可变(只读),访问或者修改array内元素的行为都不被允许,比如：array[0] = 1 (×)

3. np.column_stack(array1, array2)——将两个一维数组作为列组成一个新的二维矩阵  
   eg: 
   >>> a = np.array((1,2,3))
   >>> b = np.array((2,3,4))
   >>> np.column_stack((a,b))
   array([[1, 2],
          [2, 3],
          [3, 4]])

4. np.arctan()和np.arctan2()——二者都是反正切函数
   区别：首先，参数的个数不同——tan 为单个参数，atan2为两个参数；
         其次，对于两点形成的直线，两点分别是 point(x1,y1) 和 point(x2,y2),其斜率对应角度的计算方法可以是：
         angle = np.arctan( (y2-y1)/(x2-x1) ) 或 angle = np.arctan2( y2-y1, x2-x1 )，当 x2 - x1 = 0 时，artan需要提前判断，否则会导致错误，          但是artan2可以正常使用。
         
5. array1[array1.argmax()]——索引array1中最大值的index

6. xx, yy = [np.meshgrid](https://docs.scipy.org/doc/numpy/reference/generated/numpy.meshgrid.html)(x, y)——将x作为xx行向量，将y作为yy的列向量，生成的xx和yy的shape相同，注意：np.meshgrid(x, y)≠np.meshgrid(y, x)

7. np.innfo(np.int64)——显示机器能处理的int64型的范围

   np.finfo(np.float64)——显示机器能处理的float64型的范围
   
8. [np.set_printoptions](https://docs.scipy.org/doc/numpy/reference/generated/numpy.set_printoptions.html)(threshold = 100)——设置矩阵中元素过多时，最多可以显示100个元素，其他部分用省略号表示   

9. n = [np.argmin](https://numpy.org/devdocs/reference/generated/numpy.argmin.html)(array)——返回array所有元素中的最小值的索引（第n个）
   n = np.argmin(array, axis = 0 / 1)——返回每一行/每一列的最小值的索引（在对应行/列的第n个）

---
