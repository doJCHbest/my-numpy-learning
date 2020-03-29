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

2. np.nditer()——np.nditer作为多维数组的迭代器，这里贴出一个[数组迭代](https://docs.scipy.org/doc/numpy/reference/arrays.nditer.html#arrays-nditer)以供参考，最基本的功能是访问多维数组，直接输入一个矩阵

3. python面向对象中self和cls的简单区别：self表示一个具体的实例本身，而cls表示的是一个类本身；

4. _new_ / _init_ 的联系——通常来说：新式类开始实例化时，__new__()方法会返回cls（cls指代当前类）的实例，然后该类的__init__()方法作为构造方法会接收这个实例（即self）作为自己的第一个参数，然后依次传入__new__()方法中接收的位置参数和命名参数。注意！如果__new__()没有返回cls（即当前类）的实例，那么当前类的__init__()方法是不会被调用的。如果__new__()返回其他类（新式类或经典类均可）的实例，那么只会调用被返回的那个类的构造方法。所以在新式类中__new__()才是真正的实例化方法，为类提供外壳制造出实例框架，然后调用该框架内的构造方法__init__()使其丰满。 如果以建房子做比喻，__new__()方法负责开发地皮，打下地基，并将原料存放在工地。而__init__()方法负责从工地取材料建造出地皮开发招标书中规定的大楼，__init__()负责大楼的细节设计，建造，装修使其可交付给客户。

5. [np.bincout](https://docs.scipy.org/doc/numpy/reference/generated/numpy.bincount.html)()——这个函数是将输入的一维数组中的数字出现的次数进行统计，并且返回一个键为数字，值为数字出现次数的数组，类似于数据结构里的桶排

   eg: array = [1, 2, 3, 4, 5]
  
      array1 = [0, 0, 1, 1, 2]
      
      result = np.bincount(array1, array)
      
      解释：array按照array1的比重来分别求和，权重不同分别求和，返回的是[3, 7, 5]，例如array1[0] = 0, array1[1] = 0,所以array[0] + array[1] = 3

6. 多维数组求最后两个轴上的元素和的一种基本方法——array.sum(axis = (-1, -2))

7. 如何获取点积的对角矩阵
   
   np.diag(np.dot(A, B))——慢
   
   np.sum(A * B.T, axis = 1)——快
   
   np.einsum("ij, ji -> i", A, B)——最快
   
   附上[np.einsum()文档](https://docs.scipy.org/doc/numpy/reference/generated/numpy.einsum.html)，稍微解释一下，下列情况均相对于两个矩阵：
   
   np.einsum('ij', A)返回矩阵A本身
   
   np.einsum('ji', A)返回矩阵A的转置（等价于：A.T）
   
   np.einsum('ii', A)返回矩阵A对角线上元素的和（等价于：np.trace(A)）
   
   np.einsum('ij->', A)返回矩阵A所有元素的和（等价于：np.sum(A)）
   
   np.einsum('ij->j', A)返回矩阵A列向量的和（等价于：np.sum(A, axis=0)）
   
   np.einsum('ij->i', A)返回矩阵A行向量的和（等价于：np.sum(A, axis=1)）
   
   np.einsum('ij, ij->ij', A, B)是矩阵A和矩阵B的点乘（等价于：A*B）
   
   np.einsum('ij, jk', A, B)是矩阵A乘以矩阵B—— AB（等价于：np.dot(A, B)）

   翻译一下速度最快的例子就是A乘以B的转置，再求出结果矩阵的行向量的和
   
---
   
   
