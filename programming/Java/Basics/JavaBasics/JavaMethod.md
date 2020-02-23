# Java方法

参考资料：

> [慕课网2019Java就业班-Java 零基础入门](https://class.imooc.com/sc/64)

这是我们Java基础章节的最后一章，从下一节开始，我们将会了解到面向对象编程的核心——面向对象。但是再讲之前，在基础结构中有个东西一直没有讲到，那就是方法

## 什么是方法?

其实基本的方法我们大家都已经接触过，那就是主方法main

```java
public static void main(String[] args){
		System.out.println("HelloWorld");
	}
```

我们都知道他是一个程序的入口，除此之外，我们还接触了

```java
Scanner sc = new Scanner(System.in);
sc.nextInt();
sc.next();

System.out.println();
```

这些都是方法，我们可以看到他们都有属于自己的功能。

总结：所谓方法，就是用来解决一类问题的代码有序组合，或者说是一个功能模块，来保证[单一功能原则](https://baike.baidu.com/item/%E5%8D%95%E4%B8%80%E5%8A%9F%E8%83%BD%E5%8E%9F%E5%88%99/22718063)

## 方法声明

语法格式：

```java
访问修饰符 返回类型 方法名(参数列表){
	方法体;
}
public static void main(String[] args){
	System.out.println("HelloWorld");
}
```

public和static属于访问修饰符，他表示这个方法是一个公开的静态的方法，关于访问修饰符，在下一章面向对象中会详细讲解。

void属于返回类型，void的意思是我不返回任何值，返回类型可以是任何的数据类型，如果有返回值需要在方法体内使用return进行返回某一个量，这个量的类型必须和返回类型相同

然后main就是方法名，方法名遵循变量的命名规则，括号内是参数列表，大括号就是具体代码构成的方法体了。

## 方法分类

### 无参无返回值方法

案例导入：

![image-20200220154927210](JavaMethod.assets/image-20200220154927210.png)

案例代码：

```java
public class MethodDemo {
	public void printStar(){
        //打印输出星号的方法
		System.out.println("*******************");
	}
	public static void main(String[] args){
		MethodDemo myMethod = new MethodDemo();
        //创建MethodDemo类的对象myMethod
		myMethod.printStar();
        //使用对象调用类里的方法
		System.out.println("欢迎来到Java的世界");
		myMethod.printStar();
	}
}
```

我们把创建了一个无参无返回值的方法printStar，方法内语句是打印一排星号

应用这个方法首先需要用方法所在类去创建一个对象

```java
MethodDemo myMethod = new MethodDemo();
```

而应用的时候，就再调用，调用格式：对象名.方法

```java
myMethod.printStar();
```

### 无参带返回值方法

> 案例导入：求长方形面积的方法，并返回
>

```java
public class MethodDemo {
	public int area(){  //因为会返回整型变量所以变为int
		int lenght = 10;
		int width = 5;
		int area = lenght * width;
		return area; //返回area的值
	}
	public static void main(String[] args){
			MethodDemo myMethdemo = new MethodDemo();   //声明MethodDemo类的对象
			System.out.println(myMethdemo.area());  //打印调用area
	}
}
```

这里的输出是area方法将值返回到了主方法之后，主方法通过输出语句输出的。

### 带参无返回值方法

> 案例导入：求长方形面积的方法，需要输入长和宽

```java
public class MethodDemo {
	public void area(float a,float b){
		float lenght = a;
		float width = b;
		float area = lenght * width;
		System.out.println(area);
	}
	public static void main(String[] args){
			MethodDemo myMethdemo = new MethodDemo();   //声明MethodDemo类的对象
			myMethdemo.area(17.1f,19.2f);   //传入值为float类型
	}
}
```

### 带参带返回值方法

> 案例导入：求长方形面积的方法，需要输入长和宽，并返回

```java
public class MethodDemo {
	public float area(float a,float b){
		float lenght = a;
		float width = b;
		float area = lenght * width;
		return area; 
	}
	public static void main(String[] args){
			MethodDemo myMethdemo = new MethodDemo();   //声明MethodDemo类的对象
			float area = myMethdemo.area(17.1f,19.2f);   //传入值为float类型
			System.out.println(area);
	}
}
```

## 数组作为方法参数

使用数组作为方法参数其实适合前面大同小异

```java
public class MethodDemo {
	public void ArrayMethod(int[] arr){
		//输出打印数组值
		for(int a:arr){
			System.out.print(a+"    ");//输出a并加上空格
		}
		System.out.println();   //换行
	}
	public static void main(String[] args){
		MethodDemo am = new MethodDemo();
		int[] arr = {1,2,3,4,5,6,7,8};
		am.ArrayMethod(arr);//直接传入数组arr
	}
}
```

> 案例引入：找到数组的值

```java
import java.util.Scanner;

public class MethodDemo {
	public int[] search(int[] arr,int a){
		int[] nu=new int[arr.length];   //创建一个长度与arr相同的数组存放相同的下标值
		int nusub = 0;//初始化nu的下标
		for(int i=0;i<=arr.length-1;i++){
			if(arr[i] == a){     //数组里值是否是查找值
				nu[nusub]=i;    //将所有与a相同值的下标存放到nu里
				nusub++;    //nu下标自加
			}
		}
		return nu;
	}
	public static void main(String[] args){
		int[] arr = {8,48,68,7,54,8,67,68,15,68};   //待查询数组
		Scanner sc = new Scanner(System.in);
		int a = sc.nextInt();   //输入查询数
		MethodDemo md = new MethodDemo();
		int[] nu = md.search(arr,a);    //传入查询数组和查询数
		for(int x:nu){
			System.out.print(x+"  ");
		}
	}
}
```

## 方法重载

我们可以看到方法的分类有很多，我们通常会遇到需要传不同类型的或者说是否传值的情况，这时候需要不同的处理方式，方法重载的重要性就突出了

> 方法重载：方法名相同，参数列表不同

案例Demo

```java
public class MathDemo {

	//求两个int类型数的和
	public int plus(int m,int n){
		return m+n;
	}
	//求两个double类型数的和
	public double plus(double m,double n){
		return m+n;
	}
	//求数组元素的累加和
	public int plus(int[] arr){
		int sum=0;
		for(int i=0;i<arr.length;i++){
			sum=sum+arr[i];
		}
		return sum;
	}
	public static void main(String[] args) {
		int m=5,n=10;
		int[] arr={1,2,3,4,5,6};
		MathDemo mathDemo=new MathDemo();
		System.out.println("int类型的和："+mathDemo.plus(m, n));
		System.out.println("double类型的和："+mathDemo.plus(5.6, 7.8));
		System.out.println("数组元素的和："+mathDemo.plus(arr));
        //可以看到，因为传递参数的不同，导致他们调用的方法其实不同
	}
}

```

## 方法传值

### 基本数据类型传值

在研究这个问题之前，我们先看一串代码

```java
public class ExchangeDemo {
    //交换方法
	public void swap(int a,int b){
		int temp;
		System.out.println("交换前：a="+a+",b="+b);
		temp=a;a=b;b=temp;
		System.out.println("交换后：a="+a+",b="+b);
	}
	public void swapTest(){
		int m=4,n=5;
		System.out.println("交换前：m="+m+",n="+n);
		swap(m, n);
		System.out.println("交换后：m="+m+",n="+n);

	}
	public static void main(String[] args) {
		ExchangeDemo ed=new ExchangeDemo();
		ed.swapTest();
	}
}
```

运行结果

```
交换前：m=4,n=5
交换前：a=4,b=5
交换后：a=5,b=4
交换后：m=4,n=5
```

我们在定义mn的时候，系统首先在内存中开辟了m和n空间，把4存放在了m中，把n存放在了5中，当进行方法调用的时候，把mn的值传到了变量ab中，这时候其实只是把两个值传了过去，ab是否进行交换，是否进行操作，并不影响原本的mn。

### 数组的传值

而数组的传值又会不同

```java
public class ExchangeDemo1 {
	public void add(int n){
		n++;
		System.out.println("方法中n="+n);
	}
	public static void main(String[] args) {
		int n=10;
		System.out.println("方法调用前n的值："+n);
		ExchangeDemo1 ed1=new ExchangeDemo1();
		ed1.add(n);
		System.out.println("方法调用后n的值："+n);
	}
}
```

运行结果

```
方法调用前数组a1的元素为：
1     2     3     4     5     
数组a的元素为：
1     2     3     15     5     
方法调用后数组a1的元素为：
1     2     3     15     5  
```

我们之前说过数组是引用数据类型，在传递数组的时候，其实是将空间地址传了过去，而空间还是一样的空间，空间存放的值一旦发生改变，就会影响到其他引用同一地址空间的数组

## 可变参数列表

在很多时候，我们并不确定要接收多少个参数，这时候可变参数列表就起作用了

```java
public void sum(int... n){}
```

这就是一个基本的可见参数列表，这里int... n表示的是输入未知个数的整型

> 注意：一个方法里只能有一个可变参数列表

```java
public class ArgsDemo {
    //求和
	public void sum(int... n){
		int sum=0;
		for(int i:n){
			sum=sum+i;
		}
		System.out.println("sum="+sum);
	}
	public static void main(String[] args) {
		ArgsDemo ad=new ArgsDemo();
		ad.sum(1);
		ad.sum(1,2);
		ad.sum(1,2,3);
	}
}
```

而且可变参数列表在传入之后，会被当作一个数组处理

```java
public class ArgsDemo1 {
	//查找
    //在混合其他参数使用的时候，可变参数列表只能放在参数列的最后
	public void search(int n,int... a){
		boolean flag=false;
		for(int a1:a){
			if(a1==n){
				flag=true;break;
			}
		}
		if(flag){
			System.out.println("找到了！"+n);
		}else{
			System.out.println("没找到！"+n);
		}
	}
	
	public static void main(String[] args) {
		ArgsDemo1 ad1=new ArgsDemo1();
		ad1.search(3,1,2,3,4,5);
		int[] a={1,2,3,4,5};
		ad1.search(3, a);	//可以将数组传递给可变参数列表
	}
}
```

并且在进行重载操作的时候，可变参数列表会被当作数组，所以以下定义会被计算机认为是重复操作

```java
public void a(int n,int... a){}
public void a(int n,int[] a){}
```

> 注意：数组能够传入可变参数列表，而多个数却不能传入数组

### 方法重载

```java
public class ArgsDemo3 {
	//可变参数列表所在的方法是最后被访问的。
	/*
	public int plus(int a,int b){
		System.out.println("不带可变参数的方法被调用！");
		return a+b;
	}*/
	public int plus(int... a){
		int sum=0;
		for(int n:a){
			sum=sum+n;
		}
		System.out.println("带可变参数的方法被调用！");
		return sum;
	}
	public static void main(String[] args) {
		ArgsDemo3 ad=new ArgsDemo3();
		System.out.println("和为："+ad.plus(1,2));

	}

}
```

