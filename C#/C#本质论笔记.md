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

#### 第三章

int? count = null;引用类型赋给值类型



静态方法-实例方法





#### 本地化？