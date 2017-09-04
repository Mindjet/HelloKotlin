# Java vs. Kotlin：是时候用 Kotlin 来开发 Android 了？

说到 Android 开发，我大胆猜测你会下意识想到一种编程语言：Java。  

不可否认大部分的 Android app 都是基于 Java 编写的，但是对于Android 开发，Java 并不是唯一选择。  

其实，任何一种能在 Java 虚拟机（JVM）上运行的语言来编写 Android app。这段时间，有一种兼容 JVM 的编程语言在 Android 社区十分抢眼，它就是 JetBrains 出品的静态编程语言——Kotlin。

如果你已经对听到许多人对 Kotlin 赞不绝口并且跃跃欲试，那么时机正好。我将分为三篇文章（译者注：本文是第一篇），循序渐进地介绍和分享如何使用 Kotlin 开发 Android app。  

首先，我建议你先想一想，为什么想要从 Java 换到 Kotlin，然后我会对你的选择给出意见。  

## 怎么就要换了？

Java 是使用最广泛的编程语言之一，而且也算是 Android 开发的官方语言（译者：其实 Google 好像没有明确表示过吧）。但是，Java 并不是最佳选择，原因有很多。  

最大的原因是，Java 已经不是一种现代化语言了。尽管 Java8 加入了许多开发者翘首以盼的新特性（包括 lambda 表达式），但是在 Android 平台上只能使用一部分 Java8 的新特性，而且短时间内这种情况并不会改善。所以如果你还是用 Java 来开发 Android 的话，那估计只能跟 Java7 慢慢玩了。

并且，Java 还有许多“记录在案”的语法黑点，比如多层 `try-catch`，扩展性极差，危险的空变量（还有饱受诟病的 `NullPointerException`），就跟别说不支持函数式编程什么的了。虽然 Java 已经很积极地在添加一些函数式编程的功能，比如 lambda 表达式和函数式接口，但无济于事，因为 Java 的本来就是过程化语言。

### Kotlin 的优势

说到这里，可能有人就想换一种更加年轻的 JVM 编程语言了。刚好，Kotlin 可以无缝编译成 Java 字节码，而且自身还带有几种特质在众多 JVM 语言中脱颖而出。

####  与 Java 可互操

Kotlin 其中一项牛批的技能就是与 Java 100% 可互操（cào）。意思就是说，你可以在一个项目中一遍撸 Java，一遍撸 Kotlin，毫不违和。下面一张图，可以看到有分别用 Java 和 Kotlin 写的 `Activity`，而且用户察觉不了哪个是 Java 写的，哪个是 Kotlin 写的。

![A project consisting of a Kotlin Activity and a Java Activity](https://cms-assets.tutsplus.com/uploads/users/369/posts/27846/image/kotlin-and-java-android-project.jpeg)

既然 Kotlin 和 Java 在同一项目中可以互存，那么就不用大动手脚去把整个项目迁移到 Kotlin 上或者重开一个 Kotlin 项目，你可以直接在现有的 Java 项目上操作。  

正是有了这种互操性，我们可以直接在手头的项目中用 Kotlin 尝试开发一部分的代码，而不需要担心会影响到项目的其他部分。我们可以在保有已有 Java 代码的情况下使用 Kotlin 来开发现有项目中新的模块，或者直接一次性把整个项目迁移到 Kotlin 上。  

更加爽的是，Kotlin 可以使用几乎所有的 Java 库，甚至是基于注解处理的高级框架。

#### 平缓的学习曲线

更大程度上，Kotlin 是来增强改善 Java 的，而非把其推倒。所以，很多在 Java 中学习到的知识其实都可以应用到 Kotlin 上。  

同时，Kotlin 的设计初衷是为 Java 开发者提供平缓的学习曲线。Java 开发者其实会发现很多 Kotlin 的语法是跟 Java 很相像的，比如 Kotlin 对于一个类的声明：

```kotlin
class MainActivity : AppCompatActivity() {
```

Kotlin 也设计得比较灵性和易读，所以即使碰到一些差异很大的代码，我们还是能揣摩出代码的意思。

#### 各取所长

目前有许多编程范式，但是对于哪种是最好的，没有人能下定论。每种编程范式有利有弊，有人说函数式编程爽炸了，但也有人说过程式编程效率更高。  

所以何必孤注一掷呢？Kotlin 结合了函数式编程和过程式编程的优点，带给你丝滑般柔顺体验。  

#### 绝佳支持

Kotlin 是 JetBrains 开发的，对，Android Studio 就是基于他家的 IntelliJ 开发出来的，所以，Android Studio 平台对于 Koltin 也是有着绝佳的支持。安装完 Kotlin 插件后，点一下按钮什么的就能在项目中配置 Kotlin 了。

![You can configure your project to use Kotlin with just a few mouse clicks](https://cms-assets.tutsplus.com/uploads/users/369/posts/27846/image/android-studio-support-for-kotlin.jpeg)

在此之后，Android Studio 就绝逼会识别出 Kotlin 代码，然后编译运行。Android Studio 还为 Kotlin 提供调试，自动补全，代码搜寻，单元测试和全方位的重构支持呢。

然后，鼠标点点点，就能把 Java 文件转成 Kotlin 文件了。

#### 言简意赅的代码

那 Kotlin 和 Java 的代码一比对，会发现前者的代码比后者的简洁有力太多。言多必失的道理你我都懂啊。

举个例子，下面是一个包含 `floating action button` 的 `Activity`，但点击这个 FAB 的时候，弹出 `snackbar`：

```Java
public class MainActivity extends AppCompatActivity {
 
   @Override
   protected void onCreate(Bundle savedInstanceState) {
       super.onCreate(savedInstanceState);
       setContentView(R.layout.activity_main);
       Toolbar toolbar = (Toolbar) findViewById(R.id.toolbar);
       setSupportActionBar(toolbar);
 
       FloatingActionButton myfab = (FloatingActionButton) findViewById(R.id.myfab);
       myfab.setOnClickListener(new View.OnClickListener() {
           @Override
           public void onClick(View view) {
               Snackbar.make(view, "This is a snackbar", Snackbar.LENGTH_LONG)
                       .setAction("Action", null).show();
           }
       });
   }
 
}
```

Kotlin 相比之下就简洁许多，尤其是新建 FAB 和绑定监听器的部分：

```kotlin
class MainActivity : AppCompatActivity() {
 
   override fun onCreate(savedInstanceState: Bundle?) {
       super.onCreate(savedInstanceState)
       setContentView(R.layout.activity_main)
       val toolbar = findViewById(R.id.toolbar) as Toolbar
       setSupportActionBar(toolbar)
 
       val myfab = findViewById(R.id.myfab) as FloatingActionButton
       myfab.setOnClickListener { view ->
           Snackbar.make(view, "This is a snackbar", Snackbar.LENGTH_LONG)
                   .setAction("Action", null).show()
       }
   }
 
}
```

Kotlin 可以有效地减少样本代码的编写，与 Java 需要编写很多啰嗦的代码相比，Kotlin 有着更好的编程体验。

### 有没有坑？

没有完美的编程语言，Kotlin 也是如此。尽管它为 Android 开发者提供了很多便利，但也有一些坑我们需要注意的。

#### 增大包体积

Kotlin 的标准库和运行时会增大 apk 体积 800KB 左右。

#### 可读性

虽然说 Kotlin 的语法很优雅，但有时候我们会发现有些地方比较难看懂，毕竟我们用了很少的代码量来描述一件事情或者多件事情。Java 虽说比较冗余，但是它把事情都讲清楚了，所以在这方面，它对于陌生的代码的可读性比 Kotlin 要强。

而且，如果使用不恰当，Kotlin 操作符的重载可能会进一步降低代码的可读性。

#### ~~缺少官方的支持~~

（译者注：原文写于2016年底，我们知道今年的 IO 大会上 Kotlin 已经正式入主东宫了）

#### 资源稀缺

Kotlin 相对而言还是一个比较年轻的语言，其社区规模也比较小，特别是跟 Java 这种已经有一点年代基础的语言相比。如果你确实已经转到了 Kotlin 阵营，那么能获取到的教程、博客、开发文档、社区，比如 Stack Overflow 的支持也会相应地少一些。截至本文，Stack Overflow 上面关于 Kotlin 的 post 是 4600，而 Java 的这一数目是 100w+。

## 总结

在这篇文章中，我们思考了为什么在 Android 语言的选择上从 Java 换到了 Kotlin，也更加详细地了解了 Kotlin 这种可能替代 Java 的语言它独特的优势和劣势。



原文地址 [Java vs. Kotlin: Should You Be Using Kotlin for Android Development?](https://code.tutsplus.com/articles/java-vs-kotlin-should-you-be-using-kotlin-for-android-development--cms-27846)