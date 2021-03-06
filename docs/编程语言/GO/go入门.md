
# go命令

   
    //编译多个以go结尾的源文件，链接库文件，生成可执行文件并执行
    go run hello.go world.go
    
    //编译生成可执行文件
    go build hello.go



# 包
GO语言通过“包”组织来组织源代码，以目录结构定义包，通过`package`关键字来定义波阿，通过`import`关键字来导入包（与java类似），GO只能到如用到的包，导入多余的包也会报错。


# 变量
变量用`var`关键字声明,变量的生命周期指的是在程序运行期间变量有效存在的时间段。对于在包一级声明的变量来说，它们的生命周期和整个程序的运行周期是一致的。而相比之下，局部变量的生命周期则是动态的：每次从创建一个新变量的声明语句开始，直到该变量不再被引用为止，然后变量的存储空间可能被回收。函数的参数变量和返回值变量都是局部变量。它们在函数每次被调用的时候创建。    
那么Go语言的自动垃圾收集器是如何知道一个变量是何时可以被回收的呢？这里我们可以避开完整的技术细节，基本的实现思路是，从每个包级的变量和每个当前运行函数的每一个局部变量开始，通过指针或引用的访问路径遍历，是否可以找到该变量。如果不存在这样的访问路径，那么说明该变量是不可达的，也就是说它是否存在并不会影响程序后续的计算结果。    

因为一个变量的有效周期只取决于是否可达，因此一个循环迭代内部的局部变量的生命周期可能超出其局部作用域。同时，局部变量可能在函数返回之后依然存在。

编译器会自动选择在栈上还是在堆上分配局部变量的存储空间，但可能令人惊讶的是，这个选择并不是由用var还是new声明变量的方式决定的。

元组赋值也可以使一系列琐碎赋值更加紧凑

 ## 类型转换

对于每一个类型T，都有一个对应的类型转换操作T(x)，用于将x转为T类型（译注：如果T是指针类型，可能会需要用小括弧包装T，比如(*int)(0)）。只有当两个类型的底层基础类型相同时，才允许这种转型操作。

a :=10
b float = float(a)  //与c++中的类型转换相反，括号是括在变量名上的


Go语言将数据类型分为四类：基础类型、复合类型、引用类型和接口类型。

# 常量
常量用`const`关键字声明


# 函数
函数用`func`关键字声明，后面跟函数名，形参列表，返回值列表以及函数体，返回值列表可省略。
```
func name (parameter-list) (return-list) {
    body;
}
```

几种函数声明的方法

```
//完整声明
func min(a int,b int)(c int){return a>b?b:a}

//多个同类形参只需写一个类型，省略返回值变量名
func min(a,b int) (int) {return a>b?b:a}

//


```


go语言的代码格式要求严格，"{"必须与函数名在同一行。

go语言i++是语句不是表达式，所以不能j=i++;
go语言没有前置++语法，所以++i非法

for循环的三部分不需要括号包围。

for的三部分都可以省略，如果省略前两部分，分号也可以省略。
三部分都省略就是一个无限循环。
```
for{
    //...
}
```

i:=1是短变量声明，类型会自动推导。



# 类型
类型用`type`关键字声明

- GO语言原生支持UNICODE，可以处理全世界任何语言
- 


fmt.Printf格式化输出

```
%d          十进制整数
%x, %o, %b  十六进制，八进制，二进制整数。
%f, %g, %e  浮点数： 3.141593 3.141592653589793 3.141593e+00
%t          布尔：true或false
%c          字符（rune） (Unicode码点)
%s          字符串
%q          带双引号的字符串"abc"或带单引号的字符'c'
%v          变量的自然形式（natural format）
%T          变量的类型
%%          字面上的百分号标志（无操作数）
```