# Kotlin-2 | 集合

### 集合的声明

集合的声明使用 `mapOf`，`listOf` 和 `setOf` 等。

```kotlin
val map = mapOf<Int, Int>(0 to 1, 1 to 2, 2 to 3)
val list = listOf<Int>(0, 1, 2)
val set = setOf<Int>(0, 1, 2)
```

当然它们也可以不指定泛型，如：

```kotlin
val list = listOf(0, "string", true)
```

使用`mapOf`，`listOf` 和 `setOf` 声明的集合都不能删除或者添加元素，要想让元素可以删除和添加，应该使用对应的 `mutable` 类型的声明方式：`mutableMapOf`， `mutableListOf` 和 `mutableSetOf`。



### 集合的操作

> 在大多数遍历的操作符中，**it** 代表着当前的元素。



#### 遍历

```kotlin
val list = listOf(0, 1, 2, 3, 4, 5, 6, 7, 8, 9)

list.any { it % 5 == 0 }
list.all { it >= 0 }
list.none { it > 9 }
list.count { it % 2 == 0 }
list.fold(100) { total, next -> total + 1 }
list.foldRight(100) { next, total -> total + next }
list.reduce { total, next -> total + next }
list.reduceRight { next, total -> 1 + total }
list.forEach { println(it) }
list.forEachIndexed { index, item -> println("$index: $item") }
list.max()
list.maxBy { -it }
list.forEach {}
list.sum()
list.sumBy { it + 2 }
```

* `any`，如果集合中有任何一个元素满足条件，即返回 `true`，否则返回 `false`
* `all`，集合中所有元素满足条件才能返回 `true`，否则返回 `false`
* `none`， 与 `all` 操作符相反，当集合中所有元素逗不满足条件时才返回 `true`，否则返回 `false`
* `count`，计算集合中所有满足条件的元素数目并返回
* `fold`，提供一个初始值作为基数，然后从左往右遍历集合，回调函数中，第一个参数代表当前的基数，第二个参数代表下一个元素，回调函数中返回的值作为新的基数进行下一轮遍历，最终整个操作符返回最后的基数
* `foldRight`，与 `fold` 类似，但是方向是从右到左，并且回调函数的两个参数位置互换
* `reduce/reduceRight`，与 `fold/foldRight` 类似，但是不提供初始基数
* `forEach/forEachIndexed`，遍历/带有 `index` 的遍历，没有返回值
* `max`，顾名思义，返回集合中的最大值
* `maxBy`，根据规则计算出最大值，返回最大值的原始值
* `sum`，返回元素的总和，仅适用于 `listOf<Int>` 等可以相加的元素集合
* `sumBy`，根据提供的规则来计算总和并返回



#### 过滤

```kotlin
val list = listOf(0, 1, 2, 3, 4, 5, 6, 7, 8, 9)

list.drop(2)
list.dropLast(2)
list.dropWhile { it % 3 != 0 }
list.dropLastWhile { it % 3 != 0 }
list.filter { it % 2 == 0 }
list.filterNot { it % 2 == 0 }
list.filterNotNull()
list.take(3)
list.takeLast(4)
list.takeWhile { it < 3 }
list.takeLastWhile { it > 5 }
```

* `drop/dropLast`，舍弃掉前几个/后几个元素
* `dropWhile/dropLastWhile`，从左边/右边开始舍弃元素，直到当前元素不满足条件
* `filter`，过滤掉不满足条件的元素
* `filterNot`，与 `filter` 相反，过滤掉满足条件的元素
* `filterNotNull`，过滤掉 `null` 的元素
* `take/takeLast`，保留前几个/后几个元素
* `takeWhile/takeLastWhile`，从左边/右边开始保留元素，直到当前元素不满足条件



#### 映射

```kotlin
val list = listOf(0, 1, 2, 3, 4, 5, 6, 7, 8, 9)

list.flatMap { listOf(it, it * 2) }
list.map { listOf(it, it * 2) }
list.groupBy { if (it % 2 == 0) "even" else "odd" }
list.mapIndexed { index, item -> item + index }
```

* `flatMap`，返回一个 `list` 并插入到当前的位置中，最后返回整个变换后的 `list`
* `map`，返回一个元素（可能是 list）到当前位置，最后返回整个变换后的 `list`
* `mapIndexed`，带有 `index` 的 `map` 操作
* `groupBy`，根据规则进行分组，并返回分组后的对象

根据上面的操作，`flatMap`，`map` 和 `groupBy` 分别输出：

```kotlin
//flatMap
[0, 0, 1, 2, 2, 4, 3, 6, 4, 8, 5, 10, 6, 12, 7, 14, 8, 16, 9, 18]	
//map
[[0, 0], [1, 2], [2, 4], [3, 6], [4, 8], [5, 10], [6, 12], [7, 14], [8, 16], [9, 18]
//groupBy
{even=[0, 2, 4, 6, 8], odd=[1, 3, 5, 7, 9]}		
```

由此可以看出 `flatMap` 与 `map` 的区别，后者是直接将变换后的内容替换掉原先的位置上的内容，而前者是将变换后的内容转换成与原先位置上相同性质的内容，即原先一维 `list`，经过变换后还是一维的，这便是 `flat` 的特点所在。



#### 排序

```kotlin
val list = listOf(0, 1, 2, 3, 4, 5, 6, 7, 8, 9)

list.reversed()
list.sorted()
list.sortedBy { it % 2 }
list.sortedDescending()
```

* `sorted/reversed`，返回正序/倒序排列的集合
* `sortedBy`，根据规则进行位置排序，并返回排序后的集合
* `sortedDescending`，相当于 `reversed`



### Sum up

以上就是关于集合和集合操作的介绍，主要是关注于 `list` 的操作，若有缺漏，敬请斧正。如果你有更好的内容，欢迎补充。