# 流程控制语句

参考资料：

> [慕课网2019Java就业班-Java 零基础入门](https://class.imooc.com/sc/64)
>
> [菜鸟教程](https://www.runoob.com/java/java-basic-datatypes.html)
>
> 书籍：Java核心卷1(原书第10版)

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

嵌套结构

```java
if(判断条件1)
{
	if(判断条件2){
        ...执行语句
    }else{
        ...执行语句
    }
}else{
...执行语句
}
```

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

## 循环语句

说完条件语句，现在轮到循环的登场了，从名字可以看出，循环语句就是多次重复语句覆盖内容，可能会有小伙伴们问，我多打几次语句内容不就行了吗？

> 案例引用：假设两个数为1-100的整数，他们相乘可能是哪些值？

### while 循环

while循环是最基本的循环结构，只要while后括号内参数为真，这个循环就会一直持续

```java
while(布尔表达式) {
  //循环内容(可嵌套循环)
}
```

案例代码：

```java
public class FirstDemo {
	public static void main(String[] args){
		int a = 1;
		int b = 1;
		while(a<=100){a
			b = 1;  //把b归零
			while(b<=a){
				int c = a*b;
				System.out.println(c);
				b++;
			}
			a++;
		}
	}
}
```

代码是分别对a,b进行了1-100的循环，外层循环a，内层循环b，不过由于乘法交换位置结果不变，所以我让b<=a来减少代码运行量，然后在内层循环完成乘法然后输出

### do…while 循环

对于 while 语句而言，如果不满足条件，则不能进入循环。但有时候我们需要即使不满足条件，也至少执行一次。do…while 循环和 while 循环相似，不同的是，do…while 循环至少会执行一次。

布尔表达式在循环体的后面，所以语句块在检测布尔表达式之前已经执行了。 如果布尔表达式的值为 true，则语句块一直执行，直到布尔表达式的值为 false。

```java
do{
	//代码语句(可嵌套循环)
}while(布尔表达式);
```

案例代码：

```java
public class FirstDemo {
	public static void main(String[] args){
		int a = 1;
		int b = 1;
		do{
			b=1;
			do{
				System.out.println(a*b);
				b++;
			}while(b<=a);
			a++;
		}while(a<=100);
	}
}
```

### for循环

虽然所有循环结构都可以用 while 或者 do...while表示，但 Java 提供了另一种语句 —— for 循环，使一些循环结构变得更加简单。

for循环执行的次数是在执行前就确定的。语法格式如下：

```java
for(初始化; 布尔表达式; 更新) {
    //代码语句(可嵌套循环)
}
```

关于 for 循环有以下几点说明：

- 最先执行初始化步骤。可以声明一种类型，但可初始化一个或多个循环控制变量，也可以是空语句。
- 然后，检测布尔表达式的值。如果为 true，循环体被执行。如果为false，循环终止，开始执行循环体后面的语句。
- 执行一次循环后，更新循环控制变量。
- 再次检测布尔表达式。循环执行上面的过程。

案例代码：

```java
public class FirstDemo {
   public static void main(String[] args){
      for(int a=1;a<=100;a++){
         for(int b=1;b<=a;b++){
            System.out.println(a*b);
         }
      }
   }
}
```

#### Java 增强 for 循环

Java5 引入了一种主要用于数组的增强型 for 循环，有点类似于Python的遍历。

Java 增强 for 循环语法格式如下:

```java
for(声明语句 : 表达式) {
    //代码句子 
}
```

**声明语句：**声明新的局部变量，该变量的类型必须和数组元素的类型匹配。其作用域限定在循环语句块，其值与此时数组元素的值相等。

**表达式：**表达式是要访问的数组名，或者是返回值为数组的方法。

![img](ProcessControl.assets/A71EC47E-BC53-4923-8F88-B027937EE2FF.jpg)

Demo代码：

```java
public class Test {
   public static void main(String args[]){
      int [] numbers = {10, 20, 30, 40, 50};
 
      for(int x : numbers ){
         System.out.print( x );
         System.out.print(",");
      }
      System.out.print("\n");
      String [] names ={"James", "Larry", "Tom", "Lacy"};
      for( String name : names ) {
         System.out.print( name );
         System.out.print(",");
      }
   }
}
```

> 关于流程控制语句还有两个相关关键字比较重要
>
> [break关键字](programming/Java/Other/CommonKeywords?id=break)
>
> [continue关键字](programming/Java/Other/CommonKeywords?id=continue)