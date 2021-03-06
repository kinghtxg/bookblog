# Java数组

参考资料：

> [慕课网2019Java就业班-Java 零基础入门](https://class.imooc.com/sc/64)
>
> 书籍：Java核心卷1(原书第10版)

数组，顾名思义数据类型的组，它本身也属于一种引用数据类型，用于存储同一类型的值，然后通过整型下标，对某一具体值进行访问。

## 一维数组

> 案例引用：作为一名数学老师，要对班上五十名学生数学成绩进行输入

按照我们之前学习过的方法，我们需要定义五十个学生分别定义一个变量来进行值存储

### 声明数组

```java
数据类型[] 数组名;		//java特有格式
数据类型 数组名[];		//C\C++等共有形式
```

demo

```java
int[] a;
double b[];
char[] c;
String[] strArray;
```

声明了数组，但其实数组还不能直接使用，我们都知道声明是为了在内存中开辟一个空间出来，我们现在只告诉了计算机我们要声明一个数组，但是并没有告诉它需要多大空间。

### 创建数组

```java
/*先创建后声明*/
数组名 = new 数据类型[数组长度];
int[] arr;
arr = new int[10];	//创建一个长度为10的整型数组arr

/*创建的同时声明数组*/
数据类型[] 数组名 = new 数据类型[数组长度]
int[] arr = new int[10];	//创建一个长度为10的整型数组arr
```

完成创建之后，数组就会分配一段足够的连续的内存空间，创建之后就不能改变数组的大小

### 数组默认值

 我们在创建完变量和常量之后，是需要给它们赋值之后才能使用的，而数组则是有默认值的，因为数组本身其实是对象

- 数字数组所有元素默认值为0
- boolean数组所有元素默认值为false
- 对象数组所有元素默认值为null

### 数组初始化

在Java中提供了一种创建数组对象并同时进行赋值的简化书写形式叫做数组初始化

```java
数据类型[] 数组名 = {元素1,元素2,元素3,元素4,...,};
int[] arr = {1,2,3,4,5,6,7,8,9};
```

通过数组初始化创建的数组，数组的长度就是初始化时元素的个数，例如上述代码的创建空间大小如下

```java
int[] arr = new[9];
```

> 在Java中，允许数组长度为0，在编写一个结果为数组的方法时，如果碰巧结果为空，则这种语法形式就显得非常有用，此时可以创建一个长度为0的数组
>
> 注意：长度为0与null不同

#### 匿名数组

这种表示法可以不创建新变量就将创建一个新的数组并利用括号内提供的值进行初始化

```java
new int[] {12,54,87,35,44};
```

### 数组元素的引用

```java
数组名[下标];
```

注意：下标序号是从0开始

![image-20200219111254521](JavaArray.assets/image-20200219111254521.png)

### 数组长度.length

length属性表示数组的长度

```java
arr.length;
```

### 案例代码

```java
import java.util.Scanner;

public class FirstDemo{
	public static void main(String[] args){
		int[] student = new int[5];//为了演示方便，50个省略为5个
		Scanner sc = new Scanner(System.in);
		for(int i=0;i<student.length;i++){
			System.out.println("请输入学生成绩");
			//输入学生成绩
			student[i] = sc.nextInt();
		}
		for(int b:student){
			System.out.println(b);
			//打印所有学生成绩  //增强for循环
		}
		/*获取几号学生成绩*/
		System.out.print("获取几号学生成绩:");
		int no = sc.nextInt();
		System.out.println(no+"号学生成绩为"+student[no-1]);
	}
}
```

> 知识回顾：
>
> [增强for循环](/programming/Java/Basics/JavaBasics/ProcessControl?id=java-增强-for-循环)
>
> [Java  Scanner 类](/programming/Java/Other/class/JavaScanner?id=java-scanner-类)

## 二维数组

二维数组也是存放相同数据类型的数据，可以看成是由多个一维数组嵌套组成。

![image-20200220212200332](JavaArray.assets/image-20200220212200332.png)

> 案例引用：作为一名班主任老师，要对班上五十名学生语文、数学、外语成绩进行输入

### 声明数组

```java
数据类型[][] 数组名；
数据类型 数组名[][];
数据类型[] 数组名[];
```

demo

```java
//声明int类型的二维数组
int[][] intArray;
//声明float类型的二维数组
float floatArray[][];
//声明double类型的二维数组
double[] doubleArray[];
```

### 创建二维数组

```java
/*创建一个三行三列的int类型的数组*/
/*声明int类型的二维数组（先声明，后创建）*/
int[][] intArray;
intArray=new int[3][3];
/*声明的数组的同时进行创建*/
int[][] intArray=intArray=new int[3][3];
/*创建数组的时候，可以只指定行数
列数并没有指定，每行相当于一个一维数组，需要分别创建,每一行的数据数量是可以不相同的
*/
float[][] floatArray=newfloat[3][];
floatArray[0]=newfloat[3];//第一行有三列
floatArray[1]=newfloat[4];//第二行有四列
floatArray[2]=newfloat[5];//第三行有5列
```

### 数组元素的引用

与一维数组相似，行列的index值均从0开始

如：已知一个三行三列的整型二维数组intArray，它的第三行第二列元素表示为

```java
intArray[2][1];
```

### 二维数组的初始化

与一维数组类似，创建的同时为数组元素赋值，即为数组的初始化

```java
int[][] num={{1,2,3},{4,5,6},{7,8,9}};
```

创建了一个三行三列二维数组。num[1][2]的值为6

### 数组的遍历

多维数组，通常使用for循环嵌套的方式逐层打印

```java
public class FirstDemo{
	public static void main(String[] args){
		//初始化一个二维数组
		int[][] num1={{78,98},{65,75,63},{98}};
		//循环输出二维数组的内容
		for(int i=0;i<num1.length;i++){
			for(int j=0;j<num1[i].length;j++){
				System.out.print(num1[i][j]+"          ");
			}
			System.out.println();
		}
	}
}
```

## 数组的计算

### 数组拷贝

还记得之前说过吗？数组是引用数据类型。

在Java中允许将一个数组变量拷贝给另一个数组变量，但是，两个变量并不是复制，而是引用，对于这两个数组变量而言，他们指向了同一块内存空间，就会导致一个问题，如果一个数组的值发生改变，而另外一个数组会随之改变

![image-20200220200230995](JavaArray.assets/image-20200220200230995.png)

案例demo

```java
public class FirstDemo{
	public static void main(String[] args){
		int[] a = {1,2,3,4,5,6};
		int[] b = a;	//b数组拷贝的a
		for (int c: a) {	//打印a
			System.out.print(c);
		}
		System.out.println();   //换行
		for (int d: b) {	//打印b
			System.out.print(d);
		}
		System.out.println();   //换行
		System.out.println("修改b[3]");
		b[3] = 7;
		for (int c: a) {	//打印修改后a
			System.out.print(c);
		}
		System.out.println();   //换行
		for (int d: b) {	//打印修改后b
			System.out.print(d);
		}
	}
}
```

我们只修改了b第四个元素的值，但打印结果显示a也随着改变了

#### Arrays.copyOf

如果希望将一个数组变量的所有值拷贝到一个新的数组中，就需要用到Arrays类的copyOf方法

```java
import java.util.Arrays;

public class FirstDemo{
	public static void main(String[] args) {
		int[] a = {1,2,3,4,5,6,7,8,9,10};
		int[] b = Arrays.copyOf(a,a.length);    //第二个参数为新数组长度
		a[3] = 7;
		for (int x:a) {
			System.out.print(x+" ");
		}
		System.out.println("");
		for (int x:b) {
			System.out.print(x+" ");
		}
	}
}
```

如果新参数长度大于老参数，数组元素为数值型，那么多余的元素将会被赋值为0，数组元素是布尔型，则将赋值false，如果新参数长度小于老参数，则只拷贝前面的数据元素。

### 数组排序

#### 冒泡排序

这里介绍一下在程序当中比较经典的排序算法，叫做冒泡排序。

- 比较相邻的元素。如果第一个比第二个大，就交换他们两个。
- 对每一对相邻元素做同样的工作，从开始第一对到结尾的最后一对。在这一点，最后的元素应该会是最大的数。
- 针对所有的元素重复以上的步骤，除了最后一个。 
- 持续每次对越来越少的元素重复上面的步骤，直到没有任何一对数字需要比较

![img](JavaArray.assets/bf096b63f6246b60965c2634e6f81a4c510fa224.jpg)

```java
public class SortDemo {

	public static void main(String[] args) {
		//冒泡排序
		int[] a={34,53,12,32,56,17};
		System.out.println("排序前的数组元素为:");
		for(int n:a){
			System.out.print(n+"     ");
		}
		System.out.println();
		int temp;
		for(int i=0;i<a.length-1;i++){
			//内重循环控制每趟排序
			for(int j=0;j<a.length-i-1;j++){
				if(a[j]>a[j+1]){
					temp=a[j];
					a[j]=a[j+1];
					a[j+1]=temp;
				}
			}
		}
		System.out.println("从小到大排序后的数组元素为：");
		for(int n:a){
			System.out.print(n+"     ");
		}
	}
}
```

#### Arrays.sort

冒泡排序是经典，但却实也用的很少，而且Java本身也提供方法对数组进行排序

```java
public class FirstDemo{
	public static void main(String[] args) {
		int[] a={34,53,12,32,56,17};
		System.out.println("排序前的数组元素为:");
		for(int n:a){
			System.out.print(n+"     ");
		}
		System.out.println();
		Arrays.sort(a);	//从小到大排序
		System.out.println("从小到大排序后的数组元素为：");
		for(int n:a){
			System.out.print(n+"     ");
		}
	}
}
```

