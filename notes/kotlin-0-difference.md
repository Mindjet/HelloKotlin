# Kotlin-0 | 与Java直观的差异

### 省略分号

在 `Kotlin` 中，可以不必在语句之后加上分号，即使加上了，也会被忽略。

```kotlin
a + b = c
```



### 基本类型

`Int`，`Boolean` 和 `Long` 等是 `Kotlin` 的基本类型。



### 变量声明方式

`Kotlin` 中使用 `var` 和 `val` 来区分变量和常量，变量的数据类型声明方式也跟 `Java` 不同，而且，**变量一旦被声明一定要初始化**。

```kotlin
var a = 1
val b = 2	

var c: Int = 0
var d: String = "I am a String"
```



### 函数声明方式

`Kotlin` 中函数的声明方式比 `Java` 更加简洁。

```kotlin
fun foo0() {  
}

fun foo1(a: Int) {
}

fun foo2(a: Int): String {
    return "return String"
}
```



### 类声明方式

`Kotlin` 中类的声明方式也比 `Java` 要简洁一点。

```kotlin
class MyClass() { 
}
```

在 `Kotlin` 中，所有的类都是默认不可继承的，要想让类可以被继承 (inheritable)，要加上 `open` 关键字。

```kotlin
open class MyClass() {
}
```

### 实例化对象
在 `Kotlin` 中，初始化对象没有 `new` 关键字，或者说，在 `Kotlin` 中，压根没有 `new` 这个关键字。
```kotlin
MyClass mc = MyClass()
```


###Sum up

`Kotlin` 和 `Java` 的不同之处肯定还有很多，以上只是作为初学者在接触 `Kotlin` 时感受到的最直观的差异。

如果你有更好的内容，欢迎补充。