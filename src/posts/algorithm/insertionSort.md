---
date: 2025-05-22
category:
  - 算法与数据结构
tag:
  - 面试题
---


# 说说你对插入排序的理解？如何实现？应用场景？

 ![](https://static.vue-js.com/912adc10-267f-11ec-a752-75723a64e8f5.png)



## 一、是什么

插入排序（Insertion Sort），一般也被称为直接插入排序。对于少量元素的排序，它是一个有效、简单的算法

其主要的实现思想是将数据按照一定的顺序一个一个的插入到有序的表中，最终得到的序列就是已经排序好的数据

插入排序的工作方式像许多人排序一手扑克牌，开始时，我们的左手为空并且桌子上的牌面向下

然后，我们每次从桌子上拿走一张牌并将它插入左手中正确的位置，该正确位置需要从右到左将它与已在手中的每张牌进行比较

例如一个无序数组 3、1、7、5、2、4、9、6，将其升序的结果则如下：

一开始有序表中无数据，直接插入3

从第二个数开始，插入一个元素1，然后和有序表中记录3比较，1<3，所以插入到记录 3 的左侧

 ![](https://static.vue-js.com/9d24f5f0-267f-11ec-a752-75723a64e8f5.png)

向有序表插入记录 7 时，同有序表中记录 3 进行比较，3<7，所以插入到记录 3 的右侧

 ![](https://static.vue-js.com/a6a954e0-267f-11ec-8e64-91fdec0f05a1.png)

向有序表中插入记录 5 时，同有序表中记录 7 进行比较，5<7，同时 5>3，所以插入到 3 和 7 中间

 ![](https://static.vue-js.com/b1981940-267f-11ec-8e64-91fdec0f05a1.png)

照此规律，依次将无序表中的记录 4，9 和 6插入到有序表中

 ![](https://static.vue-js.com/bc2ed290-267f-11ec-a752-75723a64e8f5.png)

## 二、如何实现

将第一待排序序列第一个元素看做一个有序序列，把第二个元素到最后一个元素当成是未排序序列。

从头到尾依次扫描未排序序列，将扫描到的每个元素插入有序序列的适当位置

如果待插入的元素与有序序列中的某个元素相等，则将待插入元素插入到相等元素的后面

![](https://www.runoob.com/wp-content/uploads/2019/03/insertionSort.gif)

用代码表示则如下：

```js
function insertionSort(arr) {
    const len = arr.length;
    let preIndex, current;
    for (let i = 1; i < len; i++) {
        preIndex = i - 1;
        current = arr[i];
        while(preIndex >= 0 && arr[preIndex] > current) {
            arr[preIndex+1] = arr[preIndex];
            preIndex--;
        }
        arr[preIndex+1] = current;
    }
    return arr;
}
```

在插入排序中，当待排序数组是有序时，是最优的情况，只需当前数跟前一个数比较一下就可以了，这时一共需要比较`N- 1`次，时间复杂度为`O(n)`

最坏的情况是待排序数组是逆序的，此时需要比较次数最多，总次数记为：1+2+3+…+N-1，所以，插入排序最坏情况下的时间复杂度为`O(n^2)`

通过上面了解，可以看到插入排序是一种稳定的排序方式



## 三、应用场景

插入排序时间复杂度是 O(n2)，适用于数据量不大，算法稳定性要求高，且数据局部或整体有序的数列排序

## 参考文献

- https://baike.baidu.com/item/%E6%8F%92%E5%85%A5%E6%8E%92%E5%BA%8F/7214992
- http://data.biancheng.net/view/65.html