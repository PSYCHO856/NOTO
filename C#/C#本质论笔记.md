#### 第二章 数据类型

string 语法糖：字符串插值

string.format({0}{1}，a1,a2)

$"字符{变量}"



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

 引用参数 ref

输出参数 out，

1功能与ref完全一致，编译器会检查所有返回路径上是否都对out参数赋值，没有会报错

2fun(a,out _) 放弃out参数

3返回两个或多个值首先考虑元组写法

只读传引用 in

不能修改值，减少拷贝量，增强性能

返回引用？？

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

第章