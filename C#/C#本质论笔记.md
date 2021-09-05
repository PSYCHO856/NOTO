[toc]

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



#### System.Text.StringBuilder

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

第章

第章

第章 