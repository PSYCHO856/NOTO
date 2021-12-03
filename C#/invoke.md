```
OnProductSelected?.Invoke(product);
```

若event不为null，则invoke，这是C#6的新语法。 ?.称为空值传播运算符。

此处判断委托是否为空 若不为空执行委托



所有的委托类型都有一个编译器生成的`Invoke`方法。 C＃允许你调用委托本身作为调用此方法的快捷方式。

