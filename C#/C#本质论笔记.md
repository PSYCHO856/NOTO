[TOC]

#### 第二章 数据类型

string 语法糖：字符串插值

string.format({0}{1}，a1,a2)

##### $"字符{变量}"



@""内容不转义



float上限3.4E+38 10的38次方



字符串比较，区分大小写两种方法

Compare ToUpper Replace



using static System.Console;

避免前缀，

using static只支持静态方法和属性，不支持实例成员

using作用于整个命名空间



#### 字符串格式化

#### 

跨平台输出换行WriteLine()



字符串不可变

string类型不可变，修改时要将结果赋值给本身text=text.ToUpper();



字符串是不可变的对象。当我们必须执行一些操作来更改字符串或附加新字符串时，它会清除字符串对象的旧值，并在内存中创建一个新实例以将新值保存在字符串对象中。 作者：疯狂滴小黑 https://www.bilibili.com/read/cv17582918 出处：bilibili

```
using System;
namespace demoapp
{
    class StringClass
    {
        public static void main(String[] {
            string val = "Hello";
            //creates a new instance of the string
            val += "World";
            Console.WriteLine(val);
        }
    }
} 作者：疯狂滴小黑 https://www.bilibili.com/read/cv17582918 出处：bilibili

using System;
using System.Text;
namespace demoapp
{
    class StringClass
    {
        public static void main(String[] {
            StringBuilder val = new StringBuilder("Hello");
            val.Append("World");
            Console.WriteLine(val);
        }
    }
} 作者：疯狂滴小黑 https://www.bilibili.com/read/cv17582918 出处：bilibili
```

#### System.Text.StringBuilder

String a1 = "abc";　　//分配固定的内存大小
a1 += "def";　　//创建新的内存分配a1，代价比较昂贵

StringBuilder sb = new StringBuilder(20);　　//指定分配大小
sb.Append('abc');　　//分配到堆区
sb.Append('def');　　//不会被销毁，而是直接追加到后面。

namespace 计算1
{
    class Program
    {
        static void Main(string[] args)
        {
            StringBuilder sb = new StringBuilder();
            sb.Append("hello");
            sb.Append("world");
            sb.Insert(5, "_我是插入的字符_");
            Console.WriteLine(sb);

​     Console.ReadKey();

​			}

​	}

}

remove replace



String 对象是不可改变的。每次使用 System.String 类中的方法之一时，都要在[内存](https://so.csdn.net/so/search?q=%E5%86%85%E5%AD%98&spm=1001.2101.3001.7020)中创建一个新的字符串对象，这就需要为该新对象分配新的空间。在需要对字符串执行重复修改的情况下，与创建新的 String 对象相关的系统开销可能会非常昂贵。如果要修改字符串而不创建新的对象，则可以使用 System.Text.StringBuilder 类。例如，当在一个循环中将许多字符串连接在一起时，使用 StringBuilder 类可以提升性能。



https://blog.csdn.net/PEACE_FOREVER_1996/article/details/77726957



string与普通引用的区别

https://www.cnblogs.com/godshadow/p/15188828.html

当CLR初始化时，会创建一个内部的**散列表**,其中的键为字符串，值为指向托管堆中字符串的引用。刚开始,散列表为空，JIT编译器编译方法时，会在散列表中查找每一个文本常量字符串，首先会查找"abc"字符串，并且因为没有找到，编译器会在托管堆中构造一个新的指向"abc"的String对象引用，然后将"abc"字符串和指向该对象的引用添加到散列表中。
接着，在散列表中查找第二个"abc"，这一次由于找到了该字符串，所以编译器不会执行任何操作，代码中再没有其它的文本常量字符串，编译器的任务完成，代码开始执行。执行时，CLR发现第一个语句需要一个"abc"字符串引用，于是，CLR会在内部的散列表中查找"abc"，并且会找到，这样指向先前创建的String对象的引用就被保存在变量s1中，执行第二条语句时，CLR会再一次在散列表中查找"abc"，并且仍然会找到，指向同一个String对象的引用会被保存在变量s2中，到此s1和s2指向了同一个引用，所以**System.Object.Equals(s1,s2)**就会返回true了。
另外，C#中是不允许用new操作符创建String对象的，编译器会报错。



Appdent

AppendFormat

Insert

Remove

Replace



null没引用对象

void的两个含义：

标记方法不返回任何数据

指向未知类型的存储位置的一个指针



显式转型(int)



checked{



} 

unchecked

C#不允许数值类型转bool类型

隐式转型

int转long

方法转型

float.Parse(text) TryParse不会引发异常

convert ToString

double.TryParse(out double number)内联？不用提前声明number，但number只能在作用域内可用

#### 第三章 更多数据类型

int? count = null;引用类型赋给值类型

##### 元组

(string Name,string Capital,double GdpPerCapita) countryInfo = ("Malawi","Lilongwe",226.50);

静态方法-实例方法

##### 数组

交错数组定义 length返回维度
获取特定维长度用getlength
深拷贝用clone方法
普通[,] 交错[] []

字符串可以用下标访问，但不能修改单个char





#### 本地化？

#### 第四章

##### 操作符

空合并操作符??

空条件操作符?.

1使用时要长度检查（元素存在）>为空>有值 非空不代表有值，用args?.Length检查元素数量

2简化委托 PropertyChanged?.Invoke(propertyChanged(this,new PropertyChangedEventArgs(nameof(Name))))

等价于

PropertyChangedEventHandler propertyChanged = PropertyChanged;

if(propertyChanged!=null){

propertyChanged(this,new PropertyChangedEventArgs(nameof(Name))));

}

do while适用于循环至少执行一次的情况

##### C#预处理器指令

#if 指令

#elif 指令

#endif

大段代码块

#region 指令

#endregion

#### 第五章 方法和参数

命名空间 公司名-产品名-功能领域

写代码要注意可读性，而不是简短

表达式主体方法=>

C#从来不将实现与声明分开



 using和using static

#####  引用参数 ref

##### 输出参数 out，

1功能与ref完全一致，编译器会检查所有返回路径上是否都对out参数赋值，没有会报错

2fun(a,out _) 放弃out参数

3返回两个或多个值首先考虑元组写法

只读传引用 in

不能修改值，减少拷贝量，增强性能

返回引用？？

#### 第六章

##### static

静态方法 main是静态方法

静态构造函数 不显式调用 不接受参数 **不要用**

静态构造函数赋值优先于声明时赋值，同实例字段的情况一样。

最好在声明时静态初始化，而不要用静态构造函数。**用**

​	1编译器会给静态成员初始化默认值

​	2惰性初始化提升性能

**内联**方式初始化静态字段 （由编辑器决定

可声明静态属性

静态类 不可扩展派生 编辑器进行abstract sealed处理

##### 扩展方法？ 没遇到过 不会

const 包含static

##### readonly 6.0起被自动实现属性取代

 只能在构造函数和声明初始化时使用

与const比 不限于c#的字面形式值 可为自定义类 可在执行而非编译时赋值

##### 嵌套类 

可指定为private

可访问包容类的任何成员 包括private，而包容类不能访问嵌套类

##### 分部类

例子为倒水编辑器文件

好处：有工具处理的文件独立于开发者手动编写的文件

partial

不允许用分布类扩展编译好的类或其他程序集中的类。只能利用分布类在同一个程序集中将类拆分为多个文件。

##### 分部方法

只允许返回void 不允许out 返回值可以ref

ref 引用 例子 ab值交换

 

#### 第七章 继承

派生类可以直接赋给基类，因为是从属关系，直接转换，不会实例化新实例。反之不一定，需要显式转换，且运行时编译器检查，有错报错。

隐式 implicit

显式 explicit

private

protected

​	只有派生类**内部**可以访问

​	在Contact里不能PdaItem.ObjectKey 也不能Contact.ObjectKey，只能直接ObjectKey 

派生类可以作为基类来使用**扩展方法**

C#用聚合代替多继承 派生类内部定义第二个基类的实例作为关联，通过属性调用第二个基类里的字段/属性

​	缺点：需要人工添加

##### 密封类、重写基类 

override任何成员自动成为虚成员，方便后续继续重写

virtual 支持重写实例方法和属性，不支持字段和静态方法重写

运行时遇到虚方法会调用最远的实现，**即使派生类构造函数可能未执行完**。与c++相反

protected virtual

**虚暗示着实例 static virtual编译器不允许**

new 搜索从new开始的继承链 没有override定义实例方法或属性默认为new

##### base成员

使用类似this

##### 构造函数

派生类定义构造函数时**显式指定**基类构造函数

##### 抽象类

可定义virtual 但不能有实例

abstract本身就是virtual

##### System.Object

equals getHashCode GetType ReferenceEquals ToString Finalize MemberwiseClone

##### is

1判断基础类型

优点：能创建一个**显式转换失败**但**没有异常处理开销**的代码路径

2模式匹配 同1 可判断非基础类型

switch语句也支持模式匹配

##### as

尝试类型转换且不触发异常 **不能判断基础类型** 不进行非空检查 少用



#### 第八章 接口

接口也能实现多态

 所有成员都public Pascal大小写+I前缀

普通类继承抽象类，要实现其中的抽象方法，虚的不用

普通类使用接口，一定要实现所有方法

接口里不能有字段 抽象类里可以

基类和抽象类的区别 有待实现的抽象方法

8.2通过接口数组遍历了类里的数据

显式接口 只能通过接口来调用实现的方法

接口无构造器 不允许静态成员

添加额外成员会破坏版本兼容性

设计规范：优先选择类而不是接口



#### 第九章 值类型

1结构

不能定义无参构造函数

构造函数要初始化字段不是属性——避免从外包容属性外部访问字段、结构的字段初始化要求->首选只读自动实现属性而非字段

无终结器

2枚举

池 对象池 值类型

堆 引用类型





第章

第章

第章

第章

第章

第章

第章

第章

第章

第章

第章

第章

第章 

