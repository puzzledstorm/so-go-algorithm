# algorithm

## string

### 字符串的全排列

输入一个字符串，打印出该字符串中字符的所有排列。

例如输入字符串abc，则输出由字符a、b、c 所能排列出来的所有字符串

abc、acb、bac、bca、cab 和 cba。

> reference: https://github.com/julycoding/The-Art-Of-Programming-By-July-2nd/blob/master/ebook/zh/01.06.md

```python
def CalcAllPermutation(perm, start, to, p):
    if to <= 1:
        return
    if start == to:
        i = 0
        while i <= to:
            # print(perm[i])
            p.append(perm[i])
            if len(p) == 3:
                print(" ".join(p))
                p.clear()
            i += 1
    else:
        j = start
        while j <= to:
            tmp_perm = list(perm)
            tmp_perm[j], tmp_perm[start] = tmp_perm[start], tmp_perm[j]
            perm = "".join(tmp_perm)
            CalcAllPermutation(perm, start + 1, to, p)
            tmp_perm = list(perm)
            tmp_perm[j], tmp_perm[start] = tmp_perm[start], tmp_perm[j]
            perm = "".join(tmp_perm)
            j += 1

if __name__ == '__main__':
    p = []
    CalcAllPermutation("abc", 0, 2, p)
```



## list

### 寻找最小的 k 个数

输入 n 个整数，输出其中最小的 k 个。

> https://github.com/julycoding/The-Art-Of-Programming-By-July-2nd/blob/master/ebook/zh/02.01.md

方法1：快排

```python
pass
```

方法2：选择或者交换排序

```python
pass
```

方法3：更好的办法是维护容量为 k 的最大堆

```python
pass
```



方法4：快速选择算法

> smallestK代码 https://blog.csdn.net/Sgmple/article/details/110928514 
>
> https://blog.csdn.net/Dacixie/article/details/79477421
>
> 原理和图解解释： https://www.jianshu.com/p/ba148b18974f

```python
def smallestK(arr, k):
    def helper(arr, k):
        if k == 0:  # 个人感觉很有必要
            return []
        if len(arr) <= k:
            return arr
        # 快速选择
        midnum = arr[0]  # 中位数取数组第一位
        left = [e for e in arr[1:] if e <= midnum]
        len_left = len(left)  # 左数组的长度
        if len_left == k:
            return left
        elif len_left > k:
            return helper(left, k)  # 继续分
        else:  # 长度比k还小，只能把中位数右边的也加进来了
            right = [e for e in arr[1:] if e > midnum]
            return left + [midnum] + helper(right, k - len_left - 1)  # left已经被算进里面了，所以只需要在right里面找k-lenleft-1就好

    return helper(arr, k)

if __name__ == '__main__':
    a = [8, 9, 2, 3, 1, 7, 6, 33]
    kk = smallestK(a, 5)
    print(kk)
```



## sort

### 快速排序

```python
def quick_sort1(array, start, end):
    """快速排序"""
    if start >= end:  # 递归的退出条件
        return
    mid = array[start]  # 设定起始的基准元素
    low = start  # low为序列左边在开始位置的由左向右移动的游标
    high = end  # high为序列右边末尾位置的由右向左移动的游标
    while low < high:
        # 如果low与high未重合，high(右边)指向的元素大于等于基准元素，则high向左移动
        while low < high and array[high] >= mid:
            high -= 1
        print(f"high: {high}")
        array[low] = array[high]  # 走到此位置时high指向一个比基准元素小的元素,将high指向的元素放到low的位置上,此时high指向的位置空着,接下来移动low找到符合条件的元素放在此处
        # 如果low与high未重合，low指向的元素比基准元素小，则low向右移动
        print(f"h array: {array}")
        while low < high and array[low] < mid:
            low += 1
        print(f"low: {low}")
        array[high] = array[low]  # 此时low指向一个比基准元素大的元素,将low指向的元素放到high空着的位置上,此时low指向的位置空着,之后进行下一次循环,将high找到符合条件的元素填到此处
        print(f"l array: {array}")

    # 退出循环后，low与high重合，此时所指位置为基准元素的正确位置,左边的元素都比基准元素小,右边的元素都比基准元素大
    array[low] = mid  # 将基准元素放到该位置,
    # 对基准元素左边的子序列进行快速排序
    print(f"m array: {array}")

    quick_sort(array, start, low - 1)  # start :0  low -1 原基准元素靠左边一位
    # 对基准元素右边的子序列进行快速排序
    quick_sort(array, low + 1, end)  # low+1 : 原基准元素靠右一位  end: 最后
    

def test_q2():
    # array = [54, 26, 93, 17, 77, 31, 44, 55, 20]
    array = [3, 1, 7, 2, 5]
    quick_sort1(array, 0, len(array) - 1)
    print(array)


if __name__ == '__main__':
    test_q2()
```

