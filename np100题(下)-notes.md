### Numpy入门100题-后50题

---

#### 2020/3/25 51 - 60 题

1. [np.dtype](https://docs.scipy.org/doc/numpy/reference/generated/numpy.dtype.html)()——用来创建自己需要的类型

2. array.[T](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ndarray.T.html)——返回array转置后的矩阵

3. [np.atleast_2d](https://numpy.org/doc/1.18/reference/generated/numpy.atleast_2d.html)(array)——将已经二维及以上的矩阵直接返回，对不满足该条件的输入加若干个维度使其成为二维矩阵

4. array.[astype](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ndarray.astype.html)('float64')——类型的强制转换(不安全的转换)，需要注意的是，当浮点数转换成整数时，会丢失小数点后的部分，损失部分精度

5. [np.genfromtxt](https://docs.scipy.org/doc/numpy/reference/generated/numpy.genfromtxt.html#numpy.genfromtxt)()——常用的参数有：输入文件的路径path，你期望的文件的dtype，分隔符delimiter

6. 如何输出矩阵的坐标（以及值）

   1)[np.ndenumerate()](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ndenumerate.html)——需要输入矩阵
   
   2)[np.ndindex()](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ndindex.html)——需要输入矩阵的shape

7. np.random.choice(array, size, p)——从array中随机抽取size个数字，可设定抽取概率为集合p

8. [np.put](https://docs.scipy.org/doc/numpy/reference/generated/numpy.put.html)()——常用参数有：目标数组array，目标索引，需要放入的元素的矩阵

9. python中keepdim的意义：使得矩阵保持二维的特性(例如：[3, 7]和[[3, 7]])
       
10. [np.subtract](https://docs.scipy.org/doc/numpy/reference/generated/numpy.subtract.html)()——矩阵/数字的减法(取决于输入)

11. array[array[:, 1].argsort()]——对array按照第二列进行排序，即保证第二列的元素是从小到大排序的

12. [np.any](https://docs.scipy.org/doc/numpy/reference/generated/numpy.any.html)()——对给定轴的元素值是否全为0进行判断

---

#### 2020/3/29 61 - 70 题

1. [np.flat](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ndarray.flat.html)[np.abs(array - num).argmin()]——np.flat[]是一维矩阵的迭代器，比如给出样例中，找出数组array中与数字num最接近的数字

2. np.nditer([array1, array2, None])——np.nditer作为多维数组的迭代器，这里贴出一个[数组迭代](https://docs.scipy.org/doc/numpy/reference/arrays.nditer.html#arrays-nditer)以供参考
