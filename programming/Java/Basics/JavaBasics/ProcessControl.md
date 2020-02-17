# 流程控制语句

编程其实就是通过程序语言来告诉计算机每一步该做怎样的事情，计算机默认是从上而下依次执行命令，但通常我们会遇到需要重复做的事情和需要根据不同的情况来判断一些该做或者不该做的事情，这就是流程控制的工作

## 块作用域

在了解控制结构之前，我们必须搞清楚块的概念

块，指的是一个大括号括起来的若干条Java语句集合，它的本质是作用域的划分

并且块与块之间是可以嵌套的，且有嵌套关系的块内函数不允许被多次定义

例如

```java
public static void main(String[] args){
    int a = 10;
    ...
    {
        int k = 20;
        System.out.println(a);	//输出结果:a = 10
    }
    System.out.println(k);	//输出结果：报错，找不到k
}
```

上述代码中，我已经将结果给出

块的定义就是作用域，变量a所在的块嵌套了变量k所在的块，变量a的作用域是覆盖了第一条输出语句，所以能够正常输出，而变量k的值的作用域没有覆盖到输出k语句里面，所以k报错

> C++注释：在C++中，可以在嵌套的块中重定义一个变量，在内层定义的变量会覆盖在外层定义的变量，而Java不允许这样做

## 条件语句

在进行编程的时候，我们通常会遇到需要判断执行方向的情况

> 案例引用：作为收银员，顾客结账，我们需要判断他支付的金额是否足够支付商品费用？支付金额正好等于售价，予以放行。大于售价，需要找零。小于售价，需要告知顾客还需支付多少...

### if...else语句

基础结构1：

```java
if(判断条件)
{
...执行语句(若执行语句只有一句，可省略大括号);
}
```

如果判断条件成立，则执行大括号内语句，反之不执行。

基础结构2：

```java
if(判断条件)
{
...执行语句1(若执行语句只有一句，可省略大括号);
}else{
...执行语句2
}
```

如果判断条件成立，则执行大括号内语句，反之执行语句2。

基础结构3：

```java
if(判断条件1)
{
...执行语句1(若执行语句只有一句，可省略大括号);
}else if(判断条件2){
...执行语句2
}
```

如果判断条件1成立，则执行大括号内语句，反之进行判断语句2。如果2成真则执行语句2

语句内容可以无限往下延展，也可以嵌套进行。

案例代码：

```java
public class FirstDemo {
	public static void main(String[] args){
		int sellingPrice = 10; //商品售价为10
		int payMent = 14; //支付了14元
		if(sellingPrice == payMent)
		{
			System.out.println("支付完成，欢迎下次光临");
		}else if(sellingPrice > payMent){
			System.out.println("您还需要支付"+(sellingPrice-payMent)+"元");
		}else{
			System.out.println("找零"+(payMent-sellingPrice)+"元，欢迎下次光临");
		}
	}
}
```

但是，有的情况每次都进行if...else...判断又太麻烦了，会导致代码量爆炸，例如：

> 案例引用：从键盘输入1-7之间的任意数字，转换成星期进行输出

### switch结构

基础结构：

```java
switch(表达式){
    case 常量表达式1:语句1;break;
    case 常量表达式2:语句2;break;
    case 常量表达式3:语句3;break;
}
```

这个判断结构和if..else..有一定的区别，if...else...他判断的是if括号里的内容是否为真，如果是真他就执行。

switch语句则是表达式是一个常量值，当switch后括号的值和case后面的常量表达式的值相同，就执行表达式冒号后面的语句。

> 注意：我们的基本结构中使用了break语句，他的意思是，当我们执行到了break，就跳出这个结构，不再进行判断了。

案例代码：

```java
import java.util.Scanner;

public class FirstDemo {
	public static void main(String[] args){
		Scanner sc = new Scanner(System.in);
		int week = sc.nextInt();
		switch (week){
			case 1:System.out.println("Monday");break;
			case 2:System.out.println("Tuesday");break;
			case 3:System.out.println("Wednesday");break;
			case 4:System.out.println("Thursday");break;
			case 5:System.out.println("Friday");break;
			case 6:System.out.println("Saturday");break;
			case 7:System.out.println("Sunday");break;
		}
	}
}
```

> 使用Scanner对象进行数据输入
>
> [Java  Scanner 类](programming/Java/Other/class/JavaScanner)

