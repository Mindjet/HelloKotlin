# Kotlin-1 | 简洁的代码

###省略语句后的分号

```kotlin
var foo = 1
val bar = "bar"
```



### 对常用函数的封装

```kotlin
print(xxx)		//相当于 System.out.print
println(xxx)	//相当于 System.out.println
```



### 函数声明和返回值的简化

```kotlin
fun functionName()
fun functionName(){}
fun functionName(): Int{
    return 0
}
fun functionName(): Int = 0
```



### 常用结构的简化

在 `Java` 中若要新建一个实体类，常常需要写 `constructor`， `setter/getter` 和覆写 `toString()`， 但在 `Kotlin` 中，一句代码就可以搞定：

```kotlin
data class EasyPojo(var id: Int, var name: String)
```

其中，`data` 关键词会优化 `toString()` 方法使其返回友好的字符串；也可将其去掉，但 `toString()` 会返回 `类名@[hashcode]`。

但是这样子建立的实体类，其成员变量是 `public` 的，可以绕过 `setter/getter` 直接进行赋值或访问。



### λ 表达式

有一个如下的接口：

```java
public interface ICallback {
    void run();
}
```

在 `Java8` 中，实例化一个实现该接口的匿名类时，可以简化为：

```java
ICallback callback = () -> System.out.print("this is an method in an interface");
```

同样，在 `Kotlin` 中，可以将代码简化为：

```kotlin
val callback = ICallback { println("this is an method in an interface") }
```



### when 语句

`Kotlin` 引入的 `when` 语句实在解决了很多语言中 `switch/case` 语句的痛点，可以合并不同的结果，而且不用重复地写 `break`。

```Kotlin
when (x) {
        0 -> println("this is House Stark")
        1, 2 -> println("this is House Lannister")
        3, 5 -> println("this is House Baratheon")
        else -> println("this is House Targaryen")
}
```

另外，`when` 语句还可以作为一个表达式来返回数值。

```kotlin
val x: String? = null
val y = 5
val z = true
val who = when {
    x is String -> "Tyrion"
    y in 1..10 -> "Jon"
    z -> "Daenerys"
    else -> "No one"
}
```



### if 语句

跟 `when` 语句类似，`if` 语句也可以作为一个表达式来使用。

```kotlin
val x = 5
var y = if (x in 1..9) "null" else "not null"
```



### Sum up

以上就是我目前接触到的，`Kotlin` 相对于 `Java` 显得简洁的地方。如果你有更好的内容，欢迎补充。