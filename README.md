# so-go-algorithm

## 时间复杂度

## reference
```
https://labuladong.github.io/algo/di-ling-zh-bfe1b/suan-fa-sh-05f25/
https://programmercarl.com/%E5%89%8D%E5%BA%8F/%E5%85%B3%E4%BA%8E%E6%97%B6%E9%97%B4%E5%A4%8D%E6%9D%82%E5%BA%A6%EF%BC%8C%E4%BD%A0%E4%B8%8D%E7%9F%A5%E9%81%93%E7%9A%84%E9%83%BD%E5%9C%A8%E8%BF%99%E9%87%8C%EF%BC%81.html#%E4%BB%80%E4%B9%88%E6%98%AF%E5%A4%A7o
```

## 时间复杂度是什么？
大O用来表示上界的，当用它作为算法的最坏情况运行时间的上界，就是对任意数据输入的运行时间的上界。

首先看一下 Big O 记号的数学定义：
O(g(n)) = { f(n): 存在正常量 c 和 n0，使得对所有 n ≥ n0，有 0 ≤ f(n) ≤ c*g(n) }

我们常用的这个符号 O 其实代表一个函数的集合，比如 O(n^2) 代表着一个由 g(n) = n^2 派生出来的一个函数集合;

我们说一个算法的时间复杂度为 O(n^2)，意思就是描述该算法的复杂度的函数属于这个函数集合之中。

## 时间复杂度忽略常数项化简
计算时间复杂度的时候忽略常数项系数, 因为大O就是数据量级突破一个点且数据量级非常大的情况下所表现出的时间复杂度，这个数据量也就是常数项系数已经不起决定性作用的数据量。

O(1)常数阶 < O(logn)对数阶 < O(n)线性阶 < O(n^2)平方阶 < O(n^3)立方阶 < O(2^n)指数阶

## 化简例子
```
O(2N + 100) = O(N)
O(2^(N+1)) = O(2 * 2^N) = O(2^N)
O(M + 3N + 99) = O(M + N)
O(2^(2N)) = O(4^N)
O(N^3 + 999 * N^2 + 999 * N) = O(N^3)
O((N + 1) * 2^N) = O(N * 2^N + 2^N) = O(N * 2^N)
```
