---
title: JavaScript排序算法简单实现
tags:
  - 排序
  - 数组
  - 算法
categories:
  - javascript
date: 2016-09-15 16:15:31
---

使用场景：给定一个数组进行排序。下面是简陋版的实现方法，了解思路。

1、快速排序
快速排序使用分治法，把一个大串儿分为两个小串儿分别排序，在两个小串中使用递归再分串排序，最后合并。
{% codeblock lang:javascript %}
var arr = [2, -6, 8, 10, 20 - 3, -100, 203, 7, 9, 53];
function quickSort(array) {
	if (!array.length) {
		return array;
	}
        //1、选出基准
	var middleIndex = Math.floor(array.length / 2); 
	var middleItem = array.splice(middleIndex, 1); 

	var left = [];
	var right = [];
        //重新排序，比基准小的放在前，比基准大的放在后
	for (var i = 0; i &lt; array.length; i++) {
		if (array[i] &lt; middleItem[0]) {
			left.push(array[i]);
		} else {
			right.push(array[i]);
		}
	}
        //递归
	return quickSort(left).concat(middleItem, quickSort(right));
}
console.log(quickSort(arr));
{% endcodeblock %}
2、冒泡排序
冒泡排序是每次比较数组中相邻的两个元素进行比较排序。需要进行两次循环，外层循环决定循环次数，里层循环每次找到最大的值往数组后面排。
{% codeblock lang:javascript %}
var arr = [2, -6, 8, 10, 20 - 3, -100, 203, 7, 9, 53];
function bubbleSort(array) {
	for (var i = 0; i &lt; array.length - 1; i++) {
		for (var j = 0; j &lt; array.length - 1; j++) {
			if (array[j + 1] &lt; array[j]) {
				var temp;
				temp = array[j + 1];
				array[j + 1] = array[j];
				array[j] = temp;
			}
		}
	}
}
console.log(bubbleSort(arr));
{% endcodeblock %}
3、选择排序
每次循环拿出第一个元素和其他元素比较大小，对换位置。
{% codeblock lang:javascript %}
var arr = [2, -6, 8, 10, 20 - 3, -100, 203, 7, 9, 53];
function selectionSort(array) {
    var findMinIndex = function(array, start) {
        var iMin = array[start];
        var index = start;
        for (var i = start + 1; i &lt; array.length; i++) {
            if (array[i] &lt; iMin) {
                iMin = array[i];
                index = i;
            }
        }
        return index;
    };
    for (var j = 0; j &lt; array.length; j++) {
        var m = findMinIndex(array, j);
        var temp;
        temp = array[j];
        array[j] = array[m];
        array[m] = temp;
    }
    return array;
}
console.log(selectionSort(arr));
{% endcodeblock %}