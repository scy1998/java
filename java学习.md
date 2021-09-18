# java学习

**hello world**

**java语言简介**

可将java看成**类c语言**发展和衍生的产物，比如java语言的变量声明，操作符 形式，参数传递，流控制等方面和C、C++完全相同。同时java也是一个==纯粹的面向对象的程序设计语言==，它继承了C++面向对象的核心技术，**同时Java舍弃了C语言容易引起错误的指针（以引用取代）、运算符重载、多继承等特性**，==增加了垃圾回收器功能==，用于回收不再被引用的对象那个所占据的内存空间。JDK1.5又引入了泛型编程、类型安全的枚举、不定长参数和自动装/拆箱。

Java语言的特点 

1. 面向对象

   基本概念：类、对象

   三大特性：封装、继承、多态

2. 健壮性

   去掉了C/C++中指针、内存申请与释放，提供了一个相对安全的内存管理和访问机制。

3. 跨平台

   通过Java语言编写的应用程序在不同的系统平台上都可以运行。

   原因：需要运行 java程序的操作系统上，需要先安装一个Java虚拟机即JVM，由JVM来负责Java程序的运行。



==java两种核心机制==

1. Java虚拟机（JVM）
2. 垃圾收集机制 

**Java核心机制--Java虚拟机**

JVM是一个虚继的计算机，具有指令集并使用不同的存储区域。负责执行指令，管理数据、内存、寄存器。

对于不同的操作系统有不同的虚拟机

只有某平台提供了java虚拟机，java程序才能在这个平台上去运行

Java虚拟机机制屏蔽了底层运行平台的差别，实现了“一次编译 到处运行”





**Java核心机制--垃圾回收**

**不再使用的内存空间应回收--垃圾回收**

 	在C/C++中，由程序员回收无用内存

​	Java语言不用程序员回收无用空间，它提供了一种系统级线程跟踪存储空间的分配情况。在JVM空闲时，检查并释放 那些可被释放的存储空间

**JDK、JRE**

JDK（Java开发工具包）是提供给Java开发人员使用的，其中包含了Java的开发工具集，也包括了JRE。

JRE（Java运行环境）包括了java虚拟机（JVM）和Java程序所需的核心类库。

也即使用JDK的的开发工具完成Java程序，同时交给JRE去执行。



Java的三种注释方式：

1. 单行注释：//

2. 多行注释：/* */

3. 文档注释（Java特有）： /**

   ​					*/

文档注释：注释内容可以被JDK提供的工具javadoc所解析，生成一套以网页文件形式体现的该程序 的程序说明文档。

**如何从键盘获取 不同类型的变量 ：需要使用Scanner类**

具体实现步骤：

1.导包：import java.util.Scanner;

2.Scanner的实例化：Scanner scan = new Scanner（System.in）;

//注：System.in和System.out分别代表了系统标准的输入和输出设备 

3.调用Scanner类的相关方法（next()/nextInt()/nextDouble()），来获取指定类型的变量。

//注意：需要根据相应方法，来输入指定类型。如果输入的数据类型与要求的类型不匹配，会报异常：InputMisMatchException



~~~java
//1.导包：import java.util.Scanner;
import java.util.Scanner;
class ScannerTest
{
   public static  void main(String[] args)
    {
	/*	Scanner scan = new Scanner(System.in);
        int num = scan.nextInt();
        System.out.println(num);
 */
     //2.Scanner的实例化：Scanner scan = new Scanner（System.in）;
     //也即创建一个scanner对象
    Scanner scan = new Scanner(System.in);
    System.out.println("请输入你的名字： ");
      
    //3.调用Scanner类的相关方法
    String name = scan.next();
    System.out.println(name);
    
    System.out.println("请输入你的年龄： ");
    int age = scan.nextInt();
    System.out.println(age);
    
    System.out.println("请输入你的体重：");
    double weight = scan.nextDouble(weight);
    System.out.println(weight);
    
    Syestem.out,.println("你是否喜欢我？");
    boolean isLove = scan.nextBoolean();
    System.out.println("isLove");
       
    System.out.println("请输入性别：男/女");
    String gender = scan.next(); 
    char genderChar = gender.charAt(0); //获取索引为0位置上的字符
   }
}
~~~

Java随堂练习  

~~~java
import java.util.Scanner;
class  IfTest
{
    Scanner scan = new Scanner(System.in);
    System.out.println("输入成绩：");
    int score = scan.nextInt();
    if(score == 100)
    {
		System.out.println("奖励100");        
    }
    else if(score > 80 && score <=99)
    {
        System.out.println("奖励50");
    }
}
~~~



**注意：对于char型的获取，Scanner没有提供相关的方法，只能获取一个字符串**

==**eclipse快捷键使用：**==

==**shift+enter 进入新建下一行**==

==**shift+ctrl+enter 进入新建上一行**==

==**ctrl+d 删除光标所在的一行**==

**==ctrl+shift+o 快速导包==**

**==syso+alt+/ System.out.println();==**



## 数组的学习

### 一维数组

~~~java
package com.atguigu.java;

/*
 * 数组的特点：数组是有序排列的
 * 数组本身属于引用数据类型的变量。数组元素既可以是基本数据类型，也可以是引用数据类型。
 * 创建数组对象会在内存当中开辟一整个连续的内存空间
 * 数组一旦初始化，其长度是固定的。 数组的长度一旦确定，就不能改变
 * 
 * 数组的分类：
 * ①按照维数：一维数组、二维数组
 * ②按照数组元素的类型：基本数据类型元素的数组、引用数据类型的数组
 *    
 * 一维数组的初始化
 * 一维数组的声明和初始化
 不同类型的一维数组的默认初始化值
 整型：0
 浮点型：0.0
 char : 0(ascii 为 0)
 boolean：false
 引用（String类型也是引用）:null
 	
 * ②调用数组的指定位置的元素 
 * ③获取数组的长度
 * ④遍历数组
 * ⑤数组元素的默认初始化值
 * ⑥数组的内存解析
 * 
 */
public class array {
	public static void main(String[] args) {
		// ①一维数组的声明和初始化
		int num;
		num = 10;

		int[] ids; // 声明数组
		ids = new int[] { 1, 2, 3, 4 }; // 数组的静态初始化:数组的初始化和元素的赋值操作同时进行

		String[] names = new String[2];// 数组的动态初始化：数组的的初始化和数组元素的赋值分开进行

		// 错误写法
		// 1. int[] arr1 = new int[]; //既没有对数组赋初值，也没有指明数组的长度
		// 2. int[] arr2 = new int[3]{1,2,3};

		// 总结：数组一旦初始化完成，其长度就确定了 

		// ②调用数组指定位置的元素：通过角标的方式
		names[0] = " xiaoming";
		names[1] = "xiaohong";

		// ③获取数组的长度 属性length
		System.out.println(names.length);
		System.out.println(ids.length);

		// ④遍历一个数组
//		  System.out.println(names[0]); 
//		  System.out.println(names[1]);
//		  //快捷键ctrl+alt+方向键向下 复制上一行代码
		
		for(int i = 0 ; i < names.length; i++)
		{	
			 System.out.println(names[i]);
		}
		 

	}
}
~~~



二维数组

~~~Java
package com.atguigu.java;

/*
 * 二维数组的初始化
 * ①二维数组的声明和初始化
 * ②调用数组的指定位置的元素 
 * ③获取数组的长度
 * ④遍历数组
 * ⑤数组元素的默认初始化值
 * 	规定 二维数组分为外层数组的元素，内层数组的元素
 * 	int[][] arr = new int[4][3];
 * 	外层元素：arr[0], arr[1]等
 *  内层元素：arr[0][0]、arr[1][2]
 * 对于初始化方式一、如 int[][] arr = new int[4][4];
 *  外层元素的初始化值：地址值
 *  内层元素的初始化值：与一维数组情况情况相同，看内存元素是什么类型	
 *  
 * 对于初始化方式二 如 int[][] arr = new int[4][];
 *  外层元素初始化值：null
 *  内层元素初始化值：不能调用访问空指针指向的元素
 *  
 * ⑥数组的内存解析
 * 
 * */

public class multiarray {
	public static void main(String[] args) {
		//二维数组的静态初始化
		int[][] arr1 = new int[][] {{1,2,3}, {4,5}, {6,7,8}};
		//动态初始化
		String[][] arr2 = new String[3][2];
		String[][] arr3 = new String[3][];
		
		//错误写法
//		String[][] arr4 = new String[][4];
//		int[][] arr5 = new int[4][3] {{1,2,3},{4,5}, {6,7}};
		
		//正确：
		int arr4[][] = new int[][]{{1,2,3}, {4,5}};
		int[] arr5[] = {{1,2,3}, {4, 5}};
		
		arr3[1] = new String[4];
		System.out.println(arr3[1][0]);
		
		//获取数组的长度
		System.out.println(arr1.length); //二维数组的长度是3
		System.out.println(arr1[1].length);//2
		//遍历二维数组
		for(int i = 0; i < arr1.length; i++)
		{
			for(int j = 0; j < arr1[i].length; j++)
			{
				System.out.print(arr1[i][j] + " ");
			}
			System.out.println();
		}
		System.out.println("*******************");
		//数组元素的初始化值：二维数组分为外层数组的元素，内层数组的元素 
		int[][] arr11 = new int[4][3];
		System.out.println(arr11[0]); //内存的地址值
		System.out.println(arr11[0][0]);
		System.out.println("********************");
		
		int[][] arr22 = new int[4][];
		System.out.println(arr22[0]); //注意此时不是内存的地址值 而是null
		//因为此时数组内层元素没有指定，而外层元素是数组，数组是引用数据类型，数组未经过初试化默认值为null
		System.out.println(arr22[0][0]); //访问空指针中的元素，系统报错
		
	}

	
}

~~~

二维数组的内存解析如下图所示

~~~java
int[][] arr1 = new int[4][];
为二维数组开辟一块包含有四个int[]一维数组的地址空间，而外层元素没有初始化，int[]数组是引用类型默认初始值为null
~~~

arr1数组是在main方法中定义的，方法中定义的变量都是局部变量存储在栈空间当中。

new申请的空间则在堆区中 

### Arrays工具类的使用

java.util.Arrays类即为操作数组的工具类，包含了用来操作数组的各种方法。

~~~java
boolean equals(int[] a, int[] b) //判断两个数组是否相等
String toString(int[] a) //输出数组信息
void fill(int[] a, int val) //将指定元素填充到数组当中
void sort（int[] a）     //对数组进行排序
int binarySerach(int[] a, int key) //对排序后的数组进行二分法检查指定值
    
代码：
package com.atguigu.java;
import java.util.Arrays;
/*
 * 
 * java.util.Arrays:是操作数组的工具类，定义了很多操作数组的方法
 * 
 * 
 * */

public class ArraysTest {
public static void main(String[] args) {
	
	//1.boolean equals(int[] a, int[] b) //判断两个数组是否相等
	int[] arr1 = new int[] {1,2,3,4};
	int[] arr2 = new int[] {2,1,3,4};
	boolean res = Arrays.equals(arr1, arr2);
	System.out.println(res);
	
	//2.String toString(int[] a) 输出数组信息
	System.out.println(Arrays.toString(arr1));
	
	//3.void fill(int[] a, int val) 将数组中的全部元素替换成指定元素
	Arrays.fill(arr1,10);
	System.out.println(Arrays.toString(arr1));
	
	
	//4.void sort(int[] a) 底层是用的快速排序
	Arrays.sort(arr2);
	System.out.println(Arrays.toString(arr2));
	
	//5.int binarySerach(int[] a, int key) 二分查找 要求数组是有序的 查找失败返回一个负数
	int[] arr4 =new int[]{-50, -3, 5, 30, 60};
	int index = Arrays.binarySearch(arr4, 5);
	System.out.println(index);
	
}
}

~~~







~~~java
class Person
{
	//属性
    String name;
    int age = 1;
    boolean isMale;
    
    //方法
    public void eat()
    {
        System.out.println("eat food");
    }
    public void sleep()
    {
        System.out.println("sleeping");
    }
	public void  talk()
    {
        System.out.println("talking");
    }
}
~~~







### Java面向对象学习的三条主线



1.Java类及类的成员：属性、方法、构造器；代码块、内部类

2.面向对象的三大特征：封装、继承、多态

3.其他关键字：this、super、static、final、abstract、interface、package、import..



面向对象的两个要素

类：对一类事物的描述、是抽象的、概念上的

对象：是实际存在的该类事物 的每个个体、因而也称为实例



一、设计类、其实就是设计类的成员:

属性 = 成员变量 = field 

方法 = 成员方法 = 函数 = method

二、类和对象的使用（面向对象思想落地实现）
 1、创建类、设计类的成员
 2、创建类的对象
 3、通过“对象.属性”或“对象.方法” 调用对象的结构

 三、**如果创建了一个类的多个对象，则每个对象都独立的拥有一套类的属性（非static）**

如果修改一个对象的属性a,不影响另一个对象的属性a







####  类中属性的使用

####  **属性（成员变量） vs 局部变量**

1.相同点：

1.1定义变量的格式 ：数据类型 变量名 = 变量值

1.2先声明，后使用

1.3变量都有其对应的作用域



2.不同点：

2.1在类中声明的位置的不同

属性：直接定义在一对{}内

局部变量：声明在方法内、方法形参、代码块内、构造器形参、构造器内部的变量



2.2关于权限修饰符的不同

属性：可以在声明属性时，指明其权限，使用权限修饰符

常用的权限修饰符：private、public、缺省、protected                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              

局部变量：不使用权限修饰符



2.3默认初始值情况

属性：**类的属性根据其类型都有默认初始化值**

整型（byte、short、int、long）：0浮点型（float、double）：0.0

字符类型（char）：ASCII值0

boolean类型：false

==引用类型（类、数组、接口==）：null



**局部变量：没有默认初始化值 在调用局部变量之前一定要现实赋值**



2.4在内存中加载的位置不同

属性：加载到堆空间当中（非static）

局部变量：加载到栈空间







**一、理解“万事万物皆对象”** 

1.Java语言中范畴中，我们将功能、结构分装到类中，通过类的实例化，来调用具体的结构

①Scanner、String

②文件

③URL

2.涉及到java语言与前端html、后端数据库交互式时。前后端的结构在java层面都体现为类、对象。

二、内存解析的说明
 **引用类型的变量只可能存储两类值 ： null 或 地址值（含变量类型）**

 三、匿名对象的使用

 1.理解：创建的对象，没有显式地赋给一个变量，即为匿名对象
 2.特征：匿名对象只能调用一次

#### **方法的重载（overload）**

1.==定义：同一个类中，允许存在一个以上的同名方法，只要它们的参数个数或者参数类型不同即可==

"两同一不同"：同一个类、相同方法名

参数列表不同，参数个数不同，参数类型不同

2.举例： 

3.判断是否是重载：

**与方法的权限修饰符、返回值类型、形参变量名没有关系！**

4.在通过对象调用方法时	如何确定某个指定的 方法

①方法名

②参数列表



5.可变个数形参：

5.1形参格式 数据类型 ... 变量名

5.2调用可变个数形参的方法时，传入的个数可以是：0个、1个、2个....

5.3可变个数形参的方法与本类中方法名相同的，形参不同的方法之间构成重载

5.4可变个数形参形参的方法与本类中方法名相同，形参类型也相同的数组之间不会构成重载 

5.5可变个数的形参在方法的形参当中，必须声明在末尾

5.6可变个数形参在方法的形参中，最多只能声明一个可变个数形参

==可变个数形参主要用于sql语句中==

~~~java
public class overload {
//	public void getSum(int i, int j)
//	{
//		System.out.println(i + j);
//	}
//	
//	public void getSum(double d1, double d2)
//	{
//		
//	}
//	public void getSum(String s, int i)
//	{
//		
//	}
//	
//	public void getSum(int i, String s)
//	{
//		
//	}
	public static void main(String[] args) {
		
		overload test = new overload();
		test.show();
		
		test.show("hello", "world");
		test.show(new  String[] {"AA", "BB", "CC"});
		
	}
	
		//可变个数形参
		public void show(String ... args)
		{
			for(int i = 0; i < args.length; i++)
			{
				System.out.println(args[i]);
			}
		}
		
		//可变个数形参的方法与本类中方法名相同，形参类型也相同的数组之间不会构成重载
//		public void show(String[] args) 与上面public void show(Sting ... args)等同
//		{
//			
//		}
	
	
}
~~~



**关于变量的赋值：**

 	如果变量是基本数据类型，此时赋值的是变量所保存的数据值。
 	如果变量是引用数据类型，此时赋值的是变量所保存的地址值。

#### 方法形参的传递机制：值传递

1.形参：方法定义时，声明的小括号内的参数
	  实参：方法调用时，实际传给形参的值 	

2.值传递机制

 	如果参数是基本类型数据，此时实参赋给形参的是实参真实存储的数据值。
 	如果参数是引用类型数据，此时实参赋给形参的是实参存储数据的地址值或null。

~~~java
例一 public class ValueTransferTest {
	public static void main(String[] args) {
		Order order1 = new Order();
		order1.num = 100;
		//注意 类的对象是引用类型，引用类型的值只有两种 null 或 地址值
		//Order order2 = order1; 此时order2和order1的地址值相同，指向堆空间的同一个对象实体
		Order order2 = order1; 
		System.out.println("order1.num = " + order1.num + " order2.num = " + order2.num);
		//由于order2和order1的地址值相同，则改变order2所指向的对象实体,也即改变了order1所指向的对象实体
		order2.num = 200;
		System.out.println("order1.num = " + order1.num + " oorder2.num = " + order2.num);
		
		int m, n;
	 	m = 10;
		n = 20;
		System.out.println("m = " + m + " n = " + n); //m = 10 n = 20
		ValueTransferTest test = new  ValueTransferTest();
		test.swap(n, m);
		System.out.println("m = " + m + " n = " + n);  //m = 10 n = 20
		
	}
	
	public void swap(int n, int m)
	{
		int temp;
		temp = n;
		n = m;
		m = temp;
	}

}

class Order
{
	int num;
}

例二 
package com.upguigu.java;

public class ValueTransferTest1 {
	public static void main(String[] args) {
		Data data = new Data();
		data.m = 10;
		data.n = 20;
		System.out.println("m = " + data.m + " n = " + data.n);
	ValueTransferTest1 test = new ValueTransferTest1();
	test.swap(data);
	System.out.println("m = " + data.m + " n = " + data.n);
		
	}
	
	public void swap(Data data)
	{
		int temp = data.m;
		data.m = data.n;
		data.n = temp;
	}
	
}

class Data
{
	int m, n;
}



~~~

##  面向对象的特征之一：封装与隐藏

 当我i们创建一个类的对象以后，可以通过“对象.属性”的方式，对对象的属性进行赋值。
 赋值操作要受到属性的数据类型和存储范围的制约，没有其他制约条件，但在实际问题中，
 往往需要给属性赋值加入额外的限制条件。这个条件不能在属性声明时体现，只能通过
 方法进行限制条件的添加。
 需要避免用户使用对象.属性的方式对属性进行赋值，则需要将属性声明为私有的。

 二、封装性的体现
 	将类的属性私有化，同时提供公共（public）的方法来获取 (getXxx)和(setXxx)

​	此属性的值拓展、封装性的体现：①如上 ②不对外暴露的私有方法 ③单例测试...

三、封装性的体现需要权限修饰符来配合
	1.Java规定的4种权限（从小到大排列）：private 、缺省、protected、public

​	2.4种权限可以用来修饰类及类的内部结构：属性、方法、构造器、内部类
​	3.具体的，4种权限都可以用来修饰类的内部结构：属性、方法、构造器、内部类
​			修饰类只能用缺省、public
​			

	总结：Java提供了 4种权限修饰符来修饰类的内部结构，体现类及类的内部结构在被调用时可见性的大小



| 修饰符    | 类内部 | 同一个包 | 不同包的子类 | 同一个工程 |
| --------- | ------ | -------- | ------------ | ---------- |
| private   | ✔      |          |              |            |
| 缺省      | ✔      | ✔        |              |            |
| protected | ✔      | ✔        | ✔            |            |
| public    | ✔      | ✔        | ✔            | ✔          |

**一个包下定义了一个类，则不同的包下的普通类（非子类，无继承关系）要使用该类的话，不可以调用该类中声明的private、缺省、protected权限的属性、方法**

对于class的权限修饰符只可以用public和default。

1. public类可以在任意一个地方被访问
2. default类只可以被同一个包内部的类访问 



####  **类的结构：构造器（或构造方法、constructor）的使用**

 constructor ：  

 一、构造器的作用
 1.创建对象
 2.初始化对象的属性 
 	
 二 、说明
 1.如果没有显示的定义类的构造器，则系统提供一个默认构造器
 2.定义构造器的格式：权限修饰符 类名（形参列表）{}
 3.一个类中定义多个构造器，彼此构成重载
 **4.一旦程序员显示地定义了类的构造器之后了。系统就不再提供默认的空参构造器了**
 5.一个类中至少会有一个构造器



 总结：赋值构造器的先后顺序
 ①默认初始化
 ②显式初始化（类中属性被显示赋值）
 ③构造器中赋值
 ④通过对象.方法或对象.属性进行赋值

 以上操作的先后顺序：① - ② - ③ - ④

~~~java
public class PersonTest {
	public static void main(String[] args) {
		//创建类的对象：new + 构造器
		Person p = new Person();
		p.eat();
		Person p1 = new Person("Tom");
		p1.myName();
		
	}
}

class Person 
{
	int age;
	String name;
	
	//构造器
	public Person()
	{
		System.out.println("Person()");
	}
	
	public Person(String n)
	{
		name = n;
	}
	
	
	
	public void eat()
	{
		System.out.println("人吃饭");
	}
	
	public void myName()
	{
		System.out.println(name);
	}
	
~~~



####  **this关键字的使用**

 1.this可以用来修饰属性、方法、构造器

 2.this修饰属性和方法
 this理解为：当前对象或当前正在创建的对象
 	
 在类的方法中，我们可以使用“this.属性”或“this.方法”调用当前对象属性或方法 
 通过情况下 都省略"this." 特殊情况下,如果方法的形参和属性同名 必须显示的使用this.变量
 表明此变量是属性 而非形参

 **3.this调用构造器**

 ①在类的构造器中，可以显式的使用"this(形参列表)"方式，**调用本类中指定的其他构造器**
 ②构造器中不能通过"this（形参列表）"调用自己
 ③如果一个类中有n个构造器，则最多有n-1构造器中使用了"this（形参列表）"
 ④**规定使用"this(形参列表)"必须声明在当前构造器的首行**
 ⑤由④可知，当前构造器内部只能使用一次"this（形参列表）"

~~~JAVA
public class PersonTest {
	public static void main(String[] args) {
		Person person = new Person("Tom", 20); 	
	}
}

class Person{
	private String name;
	private int age;
	
	public Person() //无参构造器
	{
		this.eat();
		System.out.println("Public Person()");
	}
	
	public Person(int age)
	{
		this();          //首先调用当前对象的无参构造器
		this.age = age;
		System.out.println("public Person(int age)");
	}
	public Person(String name, int age)
	{
		this(age);           //调用含有一个整型形参的构造器
		this.name = name;
		//this.age = age;
		System.out.println("public Person(String name, int age)");
	}
	
	
	public void setName(String name)
	{
		
		this.name = name;
	}
	public String getName()
	{
		return name;
	}
	public void setAge(int age)
	{
		this.age = age; 
	}
	
	public int getAge()
	{
		return age;
	}
	
	public void eat()
	{
		System.out.println("eating ...");
	}
}
~~~





package com.atguigu.java2;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.Scanner;

import com.atguigu.java.Bank;



 **一、package关键字的使用**
1.为了更好地实现项目中类的管理，提供了包的概念
2.使用package来声明类或接口所属的包，声明在源文件的首行
3.包，属于 标识符，遵循标识符的命名规则、规范(包名一般小写)、“”
4.每.一次代表一次文件目录

补充：同一个包下，不可以命名同名的接口、类
	不同的包下，可以命名同名的接口、类
	**因为不同的包指明了不同的文件目录**	
	
**二、import关键字的使用**
import:导入
1.在源文件中显示的使用import结构导入指定包下的类、接口
2.声明在包的声明和类的声明之间 
3.如果需要导入多个结构，则并列写出
**4.可以使用xxx.*的方式 表示可以调入xxx包下的所有的内容** 
5.如果使用的类和接口是java.lang包下定义的 则可以省略import结构
6.如果使用的类或接口是本包下定义的，可以省略import结构
7.如果在源文件中，使用了不同包下的同名类，则必须至少有一个类需要以全类名的方式显示
8.如果使用xxx.方式表明可以调用xxx包下的所有结构，但如果使用xxx子包下的结构 仍需要显示地导入

*9.import static :导入指定类或接口中的静态结构：属性或方法



**Eclipse中的快捷键：** 

 * 1.补全代码的声明：alt + /

 * 2.快速修复: ctrl + 1  

 * 3.批量导包：ctrl + shift + o

 * 4.使用单行注释：ctrl + /

 * 5.使用多行注释： ctrl + shift + /   

 * 6.取消多行注释：ctrl + shift + \

 * 7.复制指定行的代码：ctrl + alt + down 或 ctrl + alt + up

 * 8.删除指定行的代码：ctrl + d

 * 9.上下移动代码：alt + up  或 alt + down

 * 10.切换到下一行代码空位：shift + enter

 * 11.切换到上一行代码空位：ctrl + shift + enter

 * 12.如何查看源码：ctrl + 选中指定的结构   或  ctrl + shift + t

 * 13.退回到前一个编辑的页面：alt + left 

 * 14.进入到下一个编辑的页面(针对于上面那条来说的)：alt + right

 * 15.光标选中指定的类，查看继承树结构：ctrl + t

 * 16.复制代码： ctrl + c

 * 17.撤销： ctrl + z

 * 18.反撤销： ctrl + y

 * 19.剪切：ctrl + x 

 * 20.粘贴：ctrl + v

 * 21.保存： ctrl + s

 * 22.全选：ctrl + a

 * 23.格式化代码： ctrl + shift + f

 * 24.选中数行，整体往后移动：tab

 * 25.选中数行，整体往前移动：shift + tab

 * 26.在当前类中，显示类结构，并支持搜索指定的方法、属性等：ctrl + o

 * 27.批量修改指定的变量名、方法名、类名等：alt + shift + r

 * 28.选中的结构的大小写的切换：变成大写： ctrl + shift + x

 * 29.选中的结构的大小写的切换：变成小写：ctrl + shift + y

 * 30.调出生成getter/setter/构造器等结构： alt + shift + s

 * 31.显示当前选择资源(工程 or 文件)的属性：alt + enter

 * 32.快速查找：参照选中的Word快速定位到下一个 ：ctrl + k

    

 * 33.关闭当前窗口：ctrl + w

 * 34.关闭所有的窗口：ctrl + shift + w

 * 35.查看指定的结构使用过的地方：ctrl + alt + g

 * 36.查找与替换：ctrl + f

 * 37.最大化当前的View：ctrl + m

 * 38.直接定位到当前行的首位：home

 * 39.直接定位到当前行的末位：end
 */



## 面向对象的特征之二：继承

 一、继承的好处：
 ①减少了代码冗余，提高了代码的复用性
 ②便于功能的拓展
 ③为多态的使用提供了前提

二、继承性的格式： class A extends B{}
A:子类、派生类、subclass
B:父类、超类、基类、superclass
2.1**子类A继承父类B以后，子类A中就获得了父类B中声明的所有属性和方法**（包括父类中的私有属性和方法）
*特别的父类中声明的private的属性和方法。子类继承后仍然获得了父类中私有的结构*
*只有因为封装性的影响，使得子类不能调用父类的结构而已*

2.2子类继承父类后 可以声明特有的属性和方法，实现功能的拓展

三、Java中关于继承的规定
1.一个类可以被多个子类继承
2.Java中单继承：一个类只能有一个父类（区别于C++）
3.子父类是相对的概念。
4.子类直接继承的父类 称为直接父类。间接继承的父类称为间接父类
5.子类继承父类之后就获取了直接父类以及所有间接父类中声明的属性和方法

 四、1.如果没有显示声明一个类的父类，则此类继承于java.lang.Object类
	2.所有java类（除java.lang.Object类）都直接或间接继承于java.lang.Object类
	3.所有的java类都具有java.lang.Object类声明的功能

####  **方法的重写（override / overwrite）**

 1.==重写：子类继承父类以后，可以对父类中同名同参数的方法进行覆盖操作==
 2.应用：**重写以后，当创建子类对象，通过子类对象调用父类中的同名同参数的方法时，**
 	**实际执行的是子类重写父类的方法。**

 3.重写的规定：
 	方法的声明：权限修饰符 返回值类型 方法名（形参列表） throws 异常的类型{
 			//方法体
 	}
 	一般将子类中称为重写的方法，父类中的称为被重写的方法
 	①子类重写的方法名和形参列表与父类被重写的方法名和形参列表相同
 	②子类重写的方法的权限修饰符**不小于**父类被重写的方法的权限修饰符
 	特殊情况：子类不能重写父类中声明为private权限的方法 
 	③返回值类型：
 	 	父类被重写的方法的返回值类型是void，则子类重写方法的返回值类型只能是void
 	 	父类被重写的方法的返回值类型是A类型，则子类重写的方法的返回值类型可以是A类或A类的子类
 		 父类被重写的方法的返回值类型是基本数据类型，则子类重写的方法的返回值类型必须是相同的基本数据类型  
 	④子类重写的方法的异常类型**不大于**父类被重写的方法抛出的异常类型
 	==**此外，子类和父类中同名同参数的方法要么都声明为非static（考虑重写），要么都声明为static（不是重写）**==
 	
 面试题：区分方法的重载与重写

1.二者的定义

2.从编译和运行的角度看

**重载允许存在多个同名的方法，而这些方法的参数不同。编译器根据方法不同的参数列表对同名的方法进行区分，调用地址在编译时就已经绑定。**

**重写属于多态，只有等到方法调用的时刻，解释运行器才确定所调用的具体的方法。称为“晚绑定”或“动态绑定”**

~~~java
/*Java的多态机制
即重写，重写主要用于子类和父类之间，在父类中定义了一个方法，同时在子类中对这个方法进行重写（函数名与形参列表相同），实现子类行为的特殊化，例如：*/
class Animal{
void eat(){ System.out.print("animal eat");}
}
class Tiger extends Animal{
void eat(){System.out.print("Tiget eat");}
}
/*子类中的eat方法即对父类的eat方法实现了重写，重写最常见的例子就是下面的声明：*/
//重写以后，当创建子类对象，通过子类对象调用父类中的同名同参数的方法时，
// 	实际执行的是子类重写父类的方法。
Animal some=new Tiger();

//注意下面的一种情况：(重写和重载的混合)
class UseAnimal{
void doStuff(Animal sa){}
void doStuff(Tiger sa){}
public static void main(String[] args){
UseAnimal ua=new UseAnimal();
Animal an=new Tiger();
ua.duStuff(an);
}
}
/*此时，调用的方法doStuff的Animal版本，因为调用重载（形参列表必须不同）方法是在编译时决定的，an的声明类型是Animal。所以调用Animal版本。
始终注意一点：重载的判断始终是在编译时决定*/
~~~



####  super关键字的使用

 1.super理解为 父类的
 2.super可以用来在子类中调用父类的属性、方法、构造器。

 3.super的使用
 	3.1  程序员可以在子类的方法和构造器中通过 super.属性 或 super.方法的方式显示调用
 		 父类中声明的属性和方法。但通常情况下习惯省略"super."
 	3.2	 特殊情况1：当子类和父类中定义了同名的属性时，要想在子类中调用父类中声明的属性，则必须
 		 显示地使用"super.属性"的方式，表明调用的是父类中属性（两个ID值）
 	3.3  特殊情况2：当子类重写了父类中的方法时，必须使用super.方法的形式表明想要调用父类中被重写的方法

 4.super调用构造器
 	4.1 可以在子类的构造器中使用"super(形参列表)"的方式，调用父类中声明的构造器
 	4.2 **super(形参列表)的使用必须声明在子类构造器的首行（与this(形参列表)相同）**，因此在类的构造器中this(形参列表)和super(形参列表)只能二选一
 	4.4 **在构造器的首行没有显式的声明this(形参列表)和super(形参列表)，则默认调用的时父类中的空参的构造器：super()**
 	4.5 在类的多个构造器中，至少有一个类的构造器使用了"super(形参列表)"调用父类中的构造器

this(形参列表)：本类重载的其他构造器

super(形参列表)：调用父类中指定的构造器

==**一个构造器的方法体中的首行不是this调用构造器就是super调用构造器，如果构造器首行两种都没显示给出，则默认使用super()**==

~~~java
Person.java
package com.atguigu.java1;

public class Person {
	String name;
	int age;
	public Person() {
		System.out.println("public Person()");
	}
	public Person(String name, int age) {
		
		this.name = name;
		this.age = age;
	}
	
	public void eat()
	{
		System.out.println("eating...");
	}
	
	public void walk(int distance)
	{
		System.out.println("walking the distance is " + distance);
	}
}

Student.java
package com.atguigu.java1;

public class Student extends Person {
	
	String major;
	
	public Student()
	{
		//super();
	}
	
	public Student(String major)
	{
		//super();
		this.major = major;
	}
	
	
	public Student(String name, int age, String major)
	{
		super(name, age);
		this.major = major;
	}
	
	public void study()
	{
		System.out.println("the major is " + major);
	}
	//对父类中的方法进行重写
	public void eat()
	{
		System.out.println("eating fruits and meats");
	}
	
	public void show()
	{
		System.out.println("name is " + name);
		System.out.println("age is " + age);
		System.out.println("major is " + major);
	}

}

StudentTest.java
public class SuperTest {
	public static void main(String[] args) {
		Student s1 = new Student("Tom", 21, "SoftWare Engineering");
		s1.show();
		Student s2 = new Student("Computer Science");
	}
}

运行结果
name is Tom
age is 21
major is SoftWare Engineering
public Person()


~~~



## 面向对象的三大特征：多态性

 1.理解多态性：可以理解为一个事物的多种形态

 2.对象的多态性：父类的引用指向子类的对象

 3.多态的使用：虚拟方法调用
 	**有了对象的多态性以后，我们在编译期只能调用父类中声明的方法，但在运行期，实际执行的是子类重写父类中的方法**
 	总结：编译看左边，运行看右边

 4.多态性的使用前提：
 ①类的继承关系
 ②方法的重写

 5.对象的多态性：**==只适用于方法，不适用于属性（当父类与子类出现同名的属性时，父类引用访问同名属性依旧访问的是自身定义的属性）==**

==注意不能通过父类的引用指向子类对象，用父类去访问子类中**特有的方法、属性**==

**如何调用子类特有的属性和方法？**
向下转型，使用强制类型转换符

（有了对象的多态性以后，内存中实际上是加载了子类特有的属性和方法，但由于变量声明为父类类型，
 	导致编译时，只能调用父类中声明的属性和方法，子类特有的属性和方法不能调用）

~~~java
 public class AnimalTest {

	public static void main(String[] args) {
		AnimalTest test = new AnimalTest();
		test.func(new Dog());
		test.func(new Cat());
	}
	public void func(Animal animal)
	{
		animal.eat();
		animal.shout();
	}
}

class Animal{
	public void eat()
	{}
	
	public void shout()
	{
		
	}
}

class Dog extends Animal{
	public void eat()
	{
		System.out.println("dog is eating...");
		
	}
	
	public void shout()
	{
		System.out.println("dog is shouting");
	}
	
}

class Cat extends Animal{
	public void eat()
	{
		System.out.println("cat is eating...");
	}
	
	public void shout() {
		System.out.println("cat is shouting...");
	}
	}
运行结果：
dog is eating...
dog is shouting
cat is eating...
cat is shouting...
~~~

 a instance of A : 判断对象a是否是A的实例。如果是 返回true 如果不是返回false
 为了在向下转型时避免出现ClassCastException的异常，在向下转型时如果返回false，不进行向下转型
 如果a instanceof A 返回true， 则 a instanceof B也返回true
 其中类B是类A的父类

~~~java
public class PersonTest {
	public static void main(String[] args) {
		//对象的多态性：父类的引用指向子类的对象
		Person p1 = new Man();
		//多态的使用：当调用子父类同名同参数的方法时，实际执行的是子类重写父类的方法
		p1.eat();
	//	p1.playGame();	注意不能访问子类中特有的方法、属性
		System.out.println("ID: " + p1.ID);
		
		//如何调用子类特有的属性和方法？
		//向下转型，使用强制类型转换符
		Man m1 = (Man)p1;
		m1.playGame();
		
		//使用强制类型有可能出现异常ClassCastException，使用instanceof在向下转型前进行判断0
		//Woman w1 = (Woman)p1;
		//w1.shopping();
		if(p1 instanceof Woman)
		{
			Woman w1 = (Woman)p1;
			w1.shopping();
		}
		if(p1 instanceof Man)
		{
			Man m2 = (Man)p1;
			m2.playGame();
		}	
	}
}
运行结果
public Person()
the man is eating
ID: 1
the man is playing games
the man is playing games

~~~

#### Object类的使用

1. object类是所有java类的根父亲

2. 如果在类的声明中未使用extends关键字指明其父亲，则默认父亲为java.lang.Object类

3. Object类中的功能（属性、方法）具有通用性
   属性：无
   方法：equals() / toString() / getClass() / hashCode() / clone() / finalize() / wait() / notify()

4. Object类只声明了一个空参构造器

面试题： == 和 equals 的区别
==：运算符

1. 可以使用在基本数据类型变量和引用数据类型中
2. 如果比较的是基本数据类型变量：比较两个变量保存的数据是否相等。（不要求数据类型相同）
   如果比较的是引用数据类型变量：比较两个  变量保存的地址值是否相等，即两个引用是否指向同一个对象实体
3. 使用==运算符必须满足符号两边的变量类型一致
   

equals()：方法
1. 是一个方法，不是运算符
2. 只能适用于引用数据类型
3. Object类中equals()的定义
	public boolean equals(Object obj)
	{
		return (this == obj);
	}
	说明Object类中定义的equals()的方法和==的作用是相同的 都是比较地址值

4. 特殊的String 、Date 、 File、包装类等都重写了Object类中equals()方法，重写以后比较的不是地址值
	而是比较的两个对象的实体内容。

5. 通常情况下，我们自定义的类如果使用equals()的话，一般是比较两个对象的“实体内容”
	就需要对Object类中的equals()进行重写

~~~java
package com.atguigu.java1;

public class Person {
	String name;
	int age;

	public Person() {
		System.out.println("public Person()");
	}
	public Person(String name, int age) {
		
		this.name = name;
		this.age = age;
	}
	
	public void eat()
	{
		System.out.println("eating...");
	}
	
	public void walk(int distance)
	{
		System.out.println("walking the distance is " + distance);
	}
	
	public boolean equals(Object obj)
	{
		if(obj == this)
			return true;
		if(obj instanceof Person)
		{
			Person p = (Person)obj;
			return p.age == this.age && this.name.equals(p.name);
		}
		return false;
	}
	
}

public class ObjectTest {
	public static void main(String[] args) {
		Person p1 = new Person("Tom", 21);
		Person p2 = new Person("Tom", 21);
		System.out.println(p1 == p2);
		System.out.println(p1.equals(p2));
		
		String str1 = new String("Tom");
		String str2 = new String("Tom");
		System.out.println(str1 == str2);
		System.out.println(str1.equals(str2));		
	}
}
运行结果
false
true
false
true

~~~



**Object类中toString()的使用**

1. 当输出一个对象的引用时，实际上是调用当前对象的toString()

2. Object类中toString()的定义
  
3. String、Date、File 、包装类等都重写了Object类中的toString()的方法

   使得在调用对象的toString() 返回“实体内容”

 4. 自定义类也可以重写toString()方法，当调用此方法时，返回对象的“实体内容”。	

    ~~~java
    public class ToString {
    	public static void main(String[] args) {
    		
    		  Person p1 = new Person("Tom", 21); 
    		  System.out.println(p1.toString());
    		  System.out.println(p1);
    		  
    		  String str = new String("man"); 
    		  System.out.println(str);
    		 
    	}
    }
    运行结果：
    
    ~~~

    

#### 包装类的理解

针对8种基本数据类型定义相应的引用数据类型==包装类（封装类）

有了类的特点，就可以调用类中的方法

| 基本数据类型 |  包装类   |
| :----------: | :-------: |
|     byte     |   Byte    |
|    short     |   Short   |
|     int      |  Integer  |
|     long     |   Long    |
|    float     |   Float   |
|    double    |  Double   |
|   boolean    |  Boolean  |
|     char     | Character |

~~~java
package com.atguigu.java2;

import java.nio.file.spi.FileSystemProvider;

/*
 包装类的使用
 1.Java提高了8种基本数据类型对应的包装类；使得基本数据类型的变量具有类的特征
 2.基本数据类型、包装类、String三者之间的相互转化
 
 
 
 
 */
public class WrapperTest {
	
	  public static void main(String[] args) { 
		  
		  WrapperTest test = new WrapperTest();
		  test.test1();
		  System.out.println("*************");
		  test.test2();
		  System.out.println("*************");
		  test.test3();
		  System.out.println("*************");
		  test.test5();
		  System.out.println("*************");
		  test.test6();
		  

	  }
	  
	  //基本数据类型--->包装类：调用包装类的构造器
	  public void test1() {
		int num1 = 10;
		Integer in1 = new Integer(num1);
		System.out.println(in1.toString());

		Integer in2 = new Integer("123");
		System.out.println(in2.toString());
		
		//报异常
//		Integer in3 = new Integer("123abc");
//		System.out.println(in3.toString());

		Float f1 = new Float(12.3f);
		System.out.println(f1.toString());
		Float f2 = new Float("12.3");
		System.out.println(f2.toString());
		
		Boolean b1 = new Boolean(true);
		Boolean b2 = new Boolean("TRue");
		System.out.println(b2.toString());
		Boolean b3 = new Boolean("123");
		System.out.println(b3.toString());
		
		Order order = new Order();
		System.out.println(order.isMale);//false
		System.out.println(order.isFemale);//null注意此时isFemale的类型是引用数据类型
	}
	  
	  //包装类--->基本数据类型：调用包装类的xxxValue()
	  public void test2()
	  {
		  Integer in1 = new Integer(12);
		  int i1 = in1.intValue();
		  System.out.println(i1);
		  
		  
	  }
	  
	  //自动装箱与自动拆箱
	  public void test3()
	  {
		  int num = 10;
		  test4(num);
		  //JKD5.0新特性
		 int num2 = 10;
		 Integer in1 = num2;//自动装箱：基本数据类型-->包装类
		 
		 boolean  b1 = true;
		 Boolean b2 = b1;
		 
		 int num3 = in1; //自动拆箱：包装类-->基本数据类型
		 
	  }
	  
	  public void test4(Object obj)
	  {
		  System.out.println(obj);
	  }
	  
	  //基本数据类型、包装类-->  String类型，调用String重载的valueOf(Xxx xxx)
	  public void test5()
	  {
		  int num1 = 10;
		  //方法1：连接运算符
		  String str1 = num1 + "";
		  
		  //方法2：调用String的valueOf()
		  float f1 = 12.3f;
		  String str2 = String.valueOf(f1);
		  System.out.println(str2);
		  
		  Double d1 = new Double(12.4);
		  String str3 = String.valueOf(d1);
		  System.out.println(str3);
		  
	  }
	  
	  //String类型-->基本数据类型、包装类:调用包装类的parseXxx(String s)
	  public void test6()
	  {
		  String str1 = "123";
		  Integer in1 = Integer.parseInt(str1);
		  System.out.println(in1);
		  
		  //错误情况
		  //int num = (int)str1;
		  //Integer num = (Integer)str1;
		  //没有父子类关系的类之间不能进行强制类型转换
		  
		  Boolean b1 = Boolean.parseBoolean(str1);
		  System.out.println(b1);
		  
	  }

}

class Order{
	boolean isMale;
	Boolean isFemale;
}

运行结果
10
123
12.3
12.3
true
false
false
null
*************
12
*************
10
*************
12.3
12.4
*************
123
false
~~~

基本数据类型、包装类与String三者之间如何转换

①自动装箱、自动拆箱

②基本数据类型、包装类-->String ：valueOf(Xxx xxx)

String-->基本数据类型、包装类：parseXxx(String s)

面试题：

~~~java
public void test（）
{
    Integer i = new Integer(1);
    Integer j = new Integer(1);
    system.out.println(i == j); //false 比较的是对象即引用类型 比较地址值
    
    //Integer的内部定义了IntegerCache结构，IntegerCache中定义了Integer[]
    //保存了从-128~127方位的整型值，如果使用自动装箱的方式，给Interger赋值的范围在
    //-128~127之间，可以直接使用数组中的元素，不用再去new了，目的是提高效率  
    Integer m = 1;
    Integer n = 1;
    System.out.println(m == n);//true
    
    Integer x = 128;
    Integer y = 128;
    System.out.println(x == y); //flase
~~~



####  static关键字的使用

 1.static：静态的
 2.static可以用来修饰属性、方法、代码块、内部类

 3.static修饰属性：静态变量（类变量）
 3.1 属性：是否使用static修饰分为：静态属性和非静态属性（实例变量）
 实例变量：当创建了类的多个对象，每个对象都独立地拥有一套类中的非静态属性。
 			当修改其中一个对象的非静态属性时，不会导致其他对象中同样的属性的修改
 静态变量：创建类的多个对象，多个对象共享同一个静态变量。
 			当通过某一个对象改变静态变量时，其他对象调用此静态变量已经是修改过。
 	
 3.2 static 修饰属性的其他说明
 ①静态变量随着类的加载而加载,可以通过"类.静态变量"的方式进行调用
 ②静态变量的加载早于对象的创建
 ③由于类只会加载一次，则静态变量在内存中只存在一份，存在方法区的静态域中
 		

 是否能调用		类变量	实例变量
 类						是			否	
 对象					是			是

3.3 静态属性举例： System.out ; Math.PI

4.使用static修饰方法
 	① 随着类的加载而加载，可以通过"类.静态方法"的方式进行调用
 	②  	是否能调用		静态方法	  非静态方法
 						类					是			否	
 						对象				是			是
 	③ 静态方法中只能调用静态的方法或属性
 		非静态方法中 既可以调用非静态的方法或属性，也可以调用静态的方法或属性

5. static的注意点
 在静态的方法内中，不能使用this、super关键字(this、super必须先创建对象，从生命周期区去理解 )
类中的常量一般也声明为static

总结：
开发中如何确定一个属性是否声明为static？
属性可以被多个对象所共享，不会随着对象的不同而不同
	
开发中如何确定一个方法是否声明为static？
操作静态属性的方法，通常设置为static
工具类中的方法 习惯上声明为static，比如Math、Arrays、Collctions

~~~java
public class StaticTest {
	public static void main(String[] args) {
		
//		  Chinese c1 = new Chinese(); 
//		  c1.name = "xiaoming";
//		  c1.age = 40;
//		  c1.nation = "China";
//		  
//		  Chinese c2 = new Chinese(); 
//		  System.out.println(c2.nation);
		 Chinese.nation = "China";
		 Chinese.show();
		
		
	}
}

class Chinese{
	String name;
	int age;
	static String nation;
	
	Chinese(){
		
	}
	
	public static void show() {
		System.out.println("I am  Chinese");
	}
}
~~~

####  单例设计模式：

1. **所谓类的单例设计模式，就是采用一定的方法保证整个软件系统中，对某个类只能存在一个对象实例**

2. 如何实现？

3.如何区分饿汉式 和 懒汉式
饿汉式：	坏处：创建类的时候已经创建了对象实体，对象加载的时间过长
		好处：饿汉式是线程安全的
		
懒汉式：	好处：延迟对象的创建
		坏处：目前的线程状态不安全--->到多线程内容时，再修改

~~~java
//单例模式类型一 饿汉式
public class SingletonTest {
	public static void main(String[] args) {
		Bank bank1 = Bank.getInstance();
		Bank bank2 = Bank.getInstance();
		System.out.println(bank1 == bank2);
	}
}

class Bank{
	//1.私有化类的构造器，防止类的外部调用从而生成对象
	private Bank()
	{
		
	}
	
	//2.内部创建类的对象,声明为私有化不允许直接调用
		//要求该对象也必须是静态的
	private static Bank instance = new Bank();
	
	//3.提供公共的方法返回类的对象，声明为static表明可以通过类名调用该方法
	public static Bank getInstance()
	{
		return instance;
	}
	
	
}

//单例模式类型二 懒汉式 
public class Singletion2 {
	public static void main(String[] args) {
		Order1 order1 = Order1.getInstance();
		Order1 order2 = Order1.getInstance();
		System.out.println(order1 == order2);
	}
}

class Order1{
	//1.私有化类的构造器
	private Order1()
	{
		
	}
	
	//2.声明当前此类对象，没有初始化
	//此对象必须声明为static
	private static Order1 instance = null;
	
	//3.声明public、static的返回当前对象的方法
	public static Order1 getInstance()
	{
		if(instance == null)
			instance = new Order1();
		return instance;
	}
}
~~~





#### 类的成员：代码块(或初始化块)

 1. 代码块的作用：用来初始化类和对象
 2. 代码块如果有修饰的话，只能使用static
 3. 分类：静态代码块 与 非静态代码块

 4.静态代码块
 	内部可以有输出语句
 	随着类的加载而自动执行**(只执行一次)**
 	作用:初始化类的信息
 	如果一个类中定义了多个静态代码块，则需要按照声明的先后顺序执行
 	静态代码块的执行优先于非静态代码块 
 	静态代码块内只能调用静态的属性、静态的方法，不能调用非静态的结构
 	
 5.非静态代码块
 	内部可以有输出语句
 	随着对象的创建而执行**(每创建一次类的对象 就执行一次)**
 	作用：可以在创建对象时，对对象的属性进行初始化
 	如果一个类定义了多个非静态代码块，则需要按照声明的先后顺序去执行
 	非静态代码块内可以调用静态的属性、静态的方法、或非静态的属性、非静态的方法

对属性赋值的位置有：
①默认初始化
②显式初始化
③构造器中初始化
④有了对象以后，可以通过"对象.属性"或"对象.方法"的方式 进行赋值
⑤在代码块中赋值



执行顺序：① - ② - ⑤ - ③ - ④

注意：父子类中静态代码块、非静态代码块、构造器的执行顺序问题
	由父及子，静态先行，代码块的执行先于构造器

~~~java
public class BlockTest {
  
	public static void main(String[] args) {
		System.out.println("*******************");
		String desc = Person.desc;
		System.out.println(desc);
		Person p1 = new Person();
		System.out.println(p1.age);
		Person p2 = new Person();
		System.out.println(p2.age);
		
	}
}

class Person{
	String name;
	int age;
	static String desc  = "I am a person";
	
	//static代码块
	static{
		desc = "i love learning";
		System.out.println("hello, static block1");
		info();
	}
	static {
		System.out.println("hello, static block2");
		
	}
	
	//代码块
	public Person()
	{
		age = 10;
		System.out.println("hello, block");
		desc = "nihao";
		info();
	}
	
	public Person(String name, int age)
	{
		this.name = name;
		this.age = age;
	}
	
	public void show()
	{
		System.out.println("name is " + name + "age is" + age);
	}
	
	public static void info()
	{
		System.out.println("public static void info()");
	}
	}
	
}
运行结果：
*******************
hello, static block1
public static void info()
hello, static block2
i love learning
hello, block
public static void info()
public Person
10
hello, block
public static void info()
public Person
10

~~~

#### final关键字

 1.final可以用来修饰的结构：类、方法、变量

 **2.final 用来修饰一个类，此类不能被其他类所继承**
 	比如：String类、System类、StringBuffer类
 	
 **3.final用来修饰方法，表明此方法不可以被重写**
 一般用于修饰父类中的方法，表明子类中不可以重写父类中的方法
 	如:object类中getClass() 

**4.final 用来修饰变量：此时的变量就称为是常量**

4.1 **final修饰属性**：可以考虑的位置：显式初始化、代码块中初始、构造器中初始化**(如果有一个构造器**
**final变量进行初始化，则所有的构造器对其都需要进行初始化)**
4.2 final修饰局部变量:
	**尤其是使用final修饰形参时,表明形参是一个常量。当我们调用此方法时，给常量形参赋一个实参，
	一旦赋值以后就只能在方法体内使用形参，不能进行重新赋值**

 **static final 用来修饰属性：全局常量**
 **注意 final修饰的变量是类的对象时，表示类的对象不可以被重新赋值，但对象的属性可以重新赋值**		

~~~java
package com.atguigu.java;

/*
 * 
 1.final可以用来修饰的结构：类、方法、变量
 
 2.final 用来修饰一个类，此类不能被其他类所继承
 	比如：String类、System类、StringBuffer类
 	
 3.final用来修饰方法，表明此方法不可以被重写
 一般用于修饰父类中的方法，表明子类中不可以重写父类中的方法
 	如:object类中getClass() 
 
 4. final 用来修饰变量：此时的变量就称为是常量
 	4.1 final修饰属性：可以考虑的位置：显式初始化、代码块中初始、构造器中初始化(如果有一个构造器
 		对final变量进行初始化，则所有的构造器对其都需要进行初始化)
 	4.2 final修饰局部变量:
 		尤其是使用final修饰形参时,表明形参是一个常量。当我们调用此方法时，给常量形参赋一个实参，
 		一旦赋值以后就只能在方法体内使用形参，不能进行重新赋值
 
 static final 用来修饰属性：全局常量
 注意 final修饰的变量是类的对象时，表示类的对象不可以被重新赋值，但对象的属性可以重新赋值			
 */
public class FinalTest {
	public static void main(String[] args) {
		FinalTest test = new FinalTest();
		Object obj = new Person1();
		Person1 p1 = (Person1)obj;
		System.out.println(p1.name);
		test.func(obj);
		Person1 p2 = (Person1)obj;
		System.out.println(p2.name);
		

		
	}
	
	final int width = 10;
	final int left;
	
	{
		left = 1;
	}
	
	public void doWidth()
	{
		//width = 20;
	}
	
	public void show()
	{
		final int num = 10; //常量
	//  num += 20;
	}
	
	public void info(final int num) {
		
	}
	
	public void func(final Object obj)
	{
		if(obj instanceof Person1)
		{
			//The final local variable obj cannot be assigned. 
			//obj = new Person();
			Person1 p1 = (Person1)obj;
			p1.name = "nihao";
		}
	}
}

class Person1 {
	public String name = "xiaoming";

}
~~~

#### static关键字的使用

 1.static：静态的
 2.static可以用来修饰属性、方法、代码块、内部类

 3.static修饰属性：静态变量（类变量）
 3.1 属性：是否使用static修饰分为：静态属性和非静态属性（实例变量）
 实例变量：当创建了类的多个变量，每个对象都独立地拥有一套类中的非静态属性。
 			当修改其中一个对象的非静态属性时，不会导致其他对象中同样的属性的修改
 静态变量：创建；类的多个对象，多个对象共享同一个静态变量。
 			当通过某一个对象改变静态变量时，其他对象调用此静态变量已经是修改过。
 	
 3.2 static 修饰属性的其他说明
 ①静态变量随着类的加载而加载,可以通过"类.静态变量"的方式进行调用
 ②静态变量的加载早于对象的创建
 ③由于类只会加载一次，则静态变量在内存中只存在一份，存在方法区的静态域中
 		
 是否能调用		类变量	实例变量
 类				是			否	
 对象			是			是
 		
3.3 静态属性举例： System.out ; Math.PI

4.使用static修饰方法
 	① 随着类的加载而加载，可以通过"类.静态方法"的方式进行调用
 	②  		是否能调用		静态方法	  非静态方法
 						类				是			否	
 					对象				是			是
 	③ 静态方法中只能调用静态的方法或属性
 		非静态方法中 既可以调用非静态的方法或属性，也可以调用静态的方法或属性

5. static的注意点
 在静态的方法内中，不能使用this、super关键字(this、super必须先创建对象，从生命周期区去理解 )
类中的常量一般也声明为static

总结：
开发中如何确定一个属性是否声明为static？
属性可以被多个对象所共享，不会随着对象的不同而不同
类中的常量也常常声明为static
	
开发中如何确定一个方法是否声明为static？
操作静态属性的方法，通常设置为static
工具类中的方法 习惯上声明为static，比如Math、Arrays、Collctions

~~~java
public class StaticTest {
	public static void main(String[] args) {
		
		  Chinese c1 = new Chinese(); 
		  c1.name = "xiaoming";
		  c1.age = 40;
		  c1.nation = "China";
		  
		  Chinese c2 = new Chinese(); 
		  System.out.println(c2.nation);
		 Chinese.nation = "China";
		 Chinese.show();
		
		
	}
}

class Chinese{
	String name;
	int age;
	static String nation;
	
	Chinese(){
		
	}
	
	public static void show() {
		System.out.println("I am  Chinese");
	}
}
运行结果
China
I am  Chinese

~~~

#### abstract关键字的使用

1.abstract：抽象的
 2.abstract可以用来修饰的结构：类、方法

 **3.abstract修饰类：抽象类**
 	**此类不能实例化**
 	**类中仍然需要构造器，便于子类实例化时调用（涉及子类对象实例化的全过程）**
 	开发中，都会提供抽象类的子类，让子类对象实例化，完成相关的操作。

 4.abstract修饰方法：抽象方法
 	抽象方法只有方法的声明，没有方法体 
 	包含抽象方法的类，一定是一个抽象类
 	反之，抽象类中可以没有抽象方法
 	**若子类重写了父类中的所有的（包括间接父类的）抽象方法后，此子类才可以实例化
 	若子类没有重写父类中所有的抽象方法。则此类是一个抽象类。需要使用abstract** 


abstract使用上的注意点：
1. abstract不能修饰属性、构造器
2. **abstract不能 修饰私有方法、静态方法（静态方法不能被重写 ）、final的方法、final的类**

~~~java
public class AbstractTest {
	public static void main(String[] args) {
		//一旦Person类抽象了 就不能实例化
		//Person p1 = new Person();
	}
}

abstract class Person{
	String name;
	int age;
	public Person()
	{
		
	}
	public Person(String name, int age)
	{
		this.name = name;
		this.age = age;
	}
	
	public void eat()
	{
		System.out.println("eating...");
	}
	
	public abstract void show();
}

class Student extends Person{
	public Student(String name, int age)
	{
		super(name, age);
	}
	
	public void show()
	{
		System.out.println("name is " + name + " age is " +  age);	
		
	}
}
~~~

#### 接口的使用：

 1. 接口使用interface来定义
 2. Java中 接口和类是两种并列的结构
 3. 如何定义接口：定义接口的成员

 	3.1 JDK7及以前：只能定义全局常量和抽象方法
 		全局常量：public static final的(但书写时可以省略不写 )
 		抽象方法：public abstract的
 		
 	3.2 JDk8：除了定义全局变量和抽象方法以外，还可以定义静态方法、默认方法

 **4.接口中不可以定义构造器！表明接口不可以实例化**

 5.Java开发中接口是通过类实现（implements）的方法来使用
 **如果实现类覆盖了接口中所有抽象的方法，则此实现类就可以实例化**
 **如果实现类没有覆盖接口中所有抽象方法。则实现类则是一个抽象类**	

 6.**java类可以实现多个接口 --->弥补了Java单继承性的局限性**
 格式 class AA extends BB implements CC,DD,EE

7.接口与接口之间可以继承，而且可以多继承

8.接口的具体使用，体现多态性
9.接口、实际上可以看做是一个规范

 面试题：抽象类与接口有那些异同 ?
 相同点：不能实例化，都可以包含抽象方法都可以被继承
 不同点：1）把抽象类和接口（Java7、Java8、Java9）的定义、内部结构解释说明
 2）类：单继承性 接口：多继承
 类与接口：多实现

 多继承和单继承

~~~JAVA
public class InerfaceTest {
	public static void main(String[] args) {
		//可以通过接口名调用静态变量
		System.out.println(Flyable.MAX_SPEED);
		System.out.println(Flyable.MIN_SPEED);
		//The final field Flyable.MIN_SPEED cannot be assigned
		//Flyable.MIN_SPEED = 2;
		Plane plane = new Plane();
		plane.fly();
	}
}

interface Flyable{
	//全局常量
	public static final int MAX_SPEED = 7900;
	int MIN_SPEED = 1;
	
	//抽象方法
	public abstract  void fly();
	//省略了public abstract
	void stop();
	
}

class Plane implements Flyable, CC{
	public void fly()
	{
		System.out.println("the plane is flying");
	}
	
	public void stop()
	{
		System.out.println("the plane is stoping");
	}
	
	public void method1()
	{}
	
	public void method2()
	{}
}

abstract class bird implements Flyable{
	public void fly()
	{
		
	}
}

interface AA{
	void method1();
}

interface BB{
	void method2();
}

interface CC extends AA, BB{
	
}
运行结果
7900
1
the plane is flying

~~~



接口的使用

1. 接口使用上也满足多态性

2. 接口实际上定义了一种规范

3. 开发中体会面向接口编程

   

~~~java
public class USBTest {
	public static void main(String[] args) {
	Computer computer = new Computer();
	//1. 创建了接口的非匿名实现类的非匿名对象
	Flash flash = new Flash();
	computer.transfer(flash);
	
	//2. 创建了接口的非匿名实现类的匿名对象
	computer.transfer(new Printer());

	//3. 创建了接口的匿名实现类的非匿名对象
	USB phone = new USB() {

		@Override
		public void start() {
			System.out.println("the phone is starting");
			
		}

		@Override
		public void end() {
			// TODO Auto-generated method stub
			System.out.println("the phone is ending...");
			
		}
	};
	
	computer.transfer(phone);
	//4. 创建了接口的匿名实现类的匿名对象
	computer.transfer(new USB(){

		@Override
		public void start() {
			// TODO Auto-generated method stub
			System.out.println("USB is staring");
		}

		@Override
		public void end() {
			// TODO Auto-generated method stub
			System.out.println("USb is ending ");
		}});
	}
}

class Computer{
	public void transfer(USB usb)
	{
		usb.start();
		System.out.println("the data is transfering...");
		usb.end();
	}
}

interface USB{
	public void start();
	
	public void end();
	
}

class Flash implements USB{
	public void start()
	{
		System.out.println("the flash is starting...");
	}
	
	public void end() {
		System.out.println("the flash is ending...");
	}
}

class Printer implements USB{
	public void start() {
		System.out.println("the Printer is starting...");
	}
	
	public void end() {
		System.out.println("the Printer is ending...");
	}
}
运行结果
the data is transfering...
the flash is ending...
the Printer is starting...
the data is transfering...
the Printer is ending...
the phone is starting
the data is transfering...
the phone is ending...
USB is staring
the data is transfering...
USb is ending 

~~~

JDk8：接口中除了定义全局变量和抽象方法以外，还可以定义静态方法、默认方法

~~~java
例
 
public interface CompareA {
	//静态方法
	public static void method1()
	{
		System.out.println("Beijing");
		
	}
	
	//默认方法
	 default void method2()
	{
		System.out.println("Shanghai");
	}
	
	default void method3() {
		System.out.println("default void method3()");
	}
}

public interface CompareB {
	default void method3() {
		System.out.println("Compare B : default void method3()");
	}
}

public class SuperClass {
	public void method3() {
		System.out.println("SuperClass : method3()");
	}
}

public class SubClassTest {
	public static void main(String[] args) {
		SubClass s  = new SubClass();
//		s.method1();
//		SubClass.method1();
		//知识点1：接口中定义的静态方法，只能通过接口调用
		CompareA.method1();
		//知识点2：通过实现类的对象，可以调用接口中默认的方法
		//如果实现类重写了接口中的默认方法，调用时仍然调用的是重写之后的方法
		s.method2();
		
		//知识点3 如果子类(或实现类)继承的父类和实现的接口中声明了同名同参的方法，
		//则子类在没有重写此方法的前提下，默认调用的是父类中的同名同参的方法
		
		//知识点4 如果实现类实现了多个接口，而这多个接口定义了同名同参的默认方法
		//那么在实现类没有重写此方法的情况下，报错：接口冲突 需要在是实现类中重写方法体
		
		s.method3();
		s.myMethod(); 
	}
}


class SubClass  extends SuperClass implements CompareA, CompareB{
	public void method2() {
		System.out.println("SubClass:method2()");
	}
	
	public void method3()
	{
		System.out.println("SubClass : method3()");
	}
	
	//知识点5 如何在子类（实现类）的方法中调用父类、接口中被重写的方法 
	public void myMethod()
	{
		method3();	//调用自己定义的重写的方法
		super.method3();	//调用父类中声明的方法
		//调用接口中的默认方法
		CompareA.super.method3();
		CompareB.super.method3();
	}
}

运行结果：
Beijing
SubClass:method2()
SubClass : method3()
SubClass : method3()
SuperClass : method3()
default void method3()
Compare B : default void method3()
    

~~~

####  类的内部成员之五：内部类

 1. Java中允许将一个类A声明在另一个类B中，则类A就是内部类，类B是外部内

 2. 内部类的分类：成员内部类 vs 局部内部类(方法内、代码块内、构造器内)

 3.成员内部类：
 	一方面作为外部类的成员：
 		①可以调用外部类的结构
 		②可以被static修饰
 		③可以被四种权限修饰

另一方面，作为一个类：
	①类内可以定义属性、方法和构造器等
	②可以被fianl修饰表示此类无法被继承
	③ 可以被abstract修饰

 4.关注如下3个问题
 4.1 如何实例化成员内部对象
 4.2 如何在成员内部类区分调用外部类结构
 4.3 开发中局部内部类的使用  

~~~java
例一
public class InnerClass {
	public static void main(String[] args) {
		//创建静态的成员内部类实例
		Person.Dog dog = new Person.Dog();
		dog.shot();
		
		//创建非静态成员内部类实例
		// Person.Bird bird = new Person.Bird();
		Person p = new Person();
		Person.Bird bird = p.new Bird();
		bird.sing();
	}
}

class Person{
	String name;
	//静态成员内部类
	static class Dog{
		public void shot() {
			System.out.println("the dog is shoting");
		}
	}
	
	class Bird{
		String name;
		public void sing() {
			System.out.println("i am singing ...");	
			Person.this.eat(); //调用外部类的非静态属性
		}
		
		public void display(String name)
		{
			System.out.println(name); //方法的形参
			System.out.println(this.name); //内部类的属性
			System.out.println(Person.this.name); // 外部类的属性
		}
		
		
	}
	
	public void Person()
	{
		//局部内部类
		class AA{
			
		}
	}
	
	public void eat() {
		System.out.println("i am eating");
	}
}

运行结果
the dog is shoting
i am singing ...
i am eating

例二  
public class InnerClassTest {

	
	/*
	 在局部内部类的方法中(比如show)如果调用局部内部类所声明的方法（如method）中的局部变量的话
	 要求此局部变量声明为final
	 
	 jdk7及之前版本，要求此局部变量显式地声明为final
	 jdk8及以后的版本，可以省略final的声明
	 */
	public void method() {
		//局部变量
		int num = 10;
		class AA{
			public void  show() {
				
				//num = 20;
				System.out.println(num);
			}
		}
	}
}            
~~~





## 异常

一、异常体系结构
java.lang.Throwable
	|------java.lang.Error：一般不编写针对性的代码进行处理
	|------Java.lang.Exception:可以进行异常的处理
		|-----编译时异常(checked)
			|-----IOException
				|-----FileNotFoundException
			|-----ClassNotFoundException
		|-----运行时异常(unchecked，RuntimeException)
			|-----NullPointerException
			|-----ArrayIndexOutofBoundsException
			|----ClassCastException
			|----NumberFormatException
			|----InputMismatchException
			|----ArithmaticException
面试题：常见的异常都有哪些？举例说明

~~~java
public class ExceptionTest {
	
	
	//****************运行时异常***********************
	//NullPointerException
	@Test
	public void test1() {
//		int[] arr = null;
//		System.out.println(arr[3]);
		String s = null;
		System.out.println(s.charAt(0));
	}
	
	//IndexOutofBoundsException
	@Test
	public void test2() {
		//ArrayIndexOutofBoundsException
//		int[] arr = new int[10];
//		System.out.println(arr[10]);
//	StringIndexOfBoundsException	
		String str = "abc";
		System.out.println(str.charAt(3));
		
	}
	
	//ClassCastException类型转换异常
	@Test
	public void test3() {
		Object obj = new Date();
		String s  = (String)obj;
		
	
	}
	
	//NumberFormatException
	@Test
	public void test4() {
		String str = "123";
		str = "abc";
		int num = Integer.parseInt(str);
		System.out.println(num);
	}
	
	//@InputMismatchException
	@Test
	public void test5() {
		Scanner scan = new Scanner(System.in);
		int score = scan.nextInt();
		System.out.println(score);		
	}
	
	//ArithmaticException
	@Test
	public void test6() {
		int a = 1;
		int b = 0;
		System.out.println(a / b);
	}
	//******************编译时异常***************
  
}
~~~

### 一、异常的处理：抓抛模型

 过程一：“抛” 
 	程序在正常执行过程中一旦出现异常，就会在异常代码出生成对应异常的对象
 	并将此对象抛出。
 	一旦抛出对象以后，其后的代码不再执行(注意理解什么是其后的代码是哪一块)
 	关于异常对象的产生：①系统自动生成的异常对象
 										②手动生成的异常对象，并抛出(throw)
 过程二：“抓”
 	①try-catch-finally
 	②throws

二、try-catch-finally的使用
try{
	//可能出现异常的代码
}catch(异常类型1 变量名1)
{
	//处理异常的方式1
}catch(异常类型2 变量名2)
{
	//处理异常的方式2
}catch(异常类型3 变量名3)
{
	//处理异常的方式3
}finally{
	//一定会执行的代码
}


说明：
1. finally是可选的
2. 使用try将可能出现的异常代码包装起来，在执行过程中，一旦出现异常，就会生成一个
	对应异常类的对象，根据此对象的类型，去catch中进行匹配
3. 一旦try中的异常对象匹配到，某一个catch时，就进入到catch中进行异常的处理，一旦处理完成以后就跳出
   当前的try-catch结构（在没有写finally的情况），继续执行其后的代码
4. ==atch中的异常类型如果没有子父类关系，则哪个声明在上，谁声明在下无所谓==
   ==catch中的异常类型如果满足子父类关系，则要求子类一定声明在父类上面==
5. 常用的异常处理方式 ：①String getMessage() ②printStackTrace()
6. ==在try结构中声明的变量，再出try结构以后就不能在被调用==
7. try-catch-finally结构可以嵌套使用

体会1：使用try-catch-finally处理编译时异常，使得程序在编译时不再报错，但运行时仍可能报错
	相当于使用try-catch-finally将一个编译时可能出现的异常延时到运行时出现。
体会2：开发中由于运行时异常比较常见，所以通常不针对运行时异常编写try-catch-finally
		针对于编译时异常，一定要考虑异常的处理。

~~~java
public class ExceptionTest1 {
	//NumberFormatException
		@Test
		public void test4() {
			String str = "123";
			str = "abc";
			try {
			int num = Integer.parseInt(str);
			System.out.println("111111111");
			}
			//
//			catch(Exception e) {
//				System.out.println("出现异常");
//			}
			catch(NullPointerException e)
			{
				System.out.println("出现空指针的异常");
			}catch(NumberFormatException e) {
				System.out.println("出现数值转换异常");
				
			}catch(Exception e) {
				System.out.println("出现异常");
			}
			//System.out.println(num);
			//num = 10;
		//	System.out.println(num);
			System.out.println("222222222222");
		}
}
运行结果
    
出现数值转换异常
222222222222

~~~

try-catch-finally中finally的使用

 1. finally是可选的
 2. finally中声明的是一定会被执行的代码，即使catch中又出现异常，try中有return语句，catch中有return语句

​        finally中的语句先于return执行

 3. 像数据库连接，输入输出流、网络编程Socket等资源，JVM是不能自动回收的，需要程序员手动进行资源的释放。此时

​       的资源释放、需要声明在finally中。

~~~java
public class FinallyTest {
	
	
	
	@Test
	public void testMethod() {
		int num = method();
		System.out.println(num);
	}
	
	public int method() {
		try {
			int[] arr = new int[10];
			System.out.println(arr[10]);
			return 1;
		}catch(ArrayIndexOutOfBoundsException e) {
			e.printStackTrace();
			 return 2;
		}finally {
			System.out.println("1111111111");
		
		}
		
	}
运行结果
java.lang.ArrayIndexOutOfBoundsException: 10
1111111111
2
	
	@Test
	public void test1() {
		try {
			int a = 10;
			int b = 0;
			System.out.println(a / b);	
			
		}catch(ArithmeticException e)
		{
			e.printStackTrace();
			
		}catch(Exception e) {
			e.printStackTrace();
		}finally {
			System.out.println("111111111");
		}	
		
	}
}

运行结果：
java.lang.ArithmeticException: / by zero
111111111
~~~

**异常处理方式二：throws + 异常类型**

1. "throws + 异常类型"写在方法声明处。指明此方法执行时，可能会抛出的异常

 	一旦当方法体执行时，出现异常，仍会在异常代码处生成一个异常类的对象。此对象满足
 	throws后异常类型时，就会被抛出。方法体中异常代码后续的代码就不再执行

 












2. 体会：try-catch-finally：真正的将异常给处理掉了

 	throws只是将异常抛给了方法的调用者，并没有将异常处理掉

3. 开发中如何选择使用try-catch-finally还是使用throws？
    3.1 如果父类中被重写的方法没有throws方式处理异常，则子类重写的地方也不能用throws，意味着如果

  	  子类重写的方法中有异常，必须使用try-catch-finally方式去处理
  3.2 执行的方法中，先后又调用了另外几个方法，这几个方法是递进关系。建议这几个方法用throws
  	   的方式进行处理。而执行的方法a可以考虑使用try-catch-finally方式进行处理。


 面试题：
 throw 和 throws的区别
 throw表示抛出一个异常类的对象，生成异常对象的过程，声明在方法体内
 throws属于异常处理的一种方式，声明在方法的声明处



方法重写的规则之一
子类重写的方法抛出的异常类型不大于父类被重写的方法抛出的异常

~~~java
public class ExceptionTest2 {
	public static void main(String[] args) {
		  ExceptionTest2 test = new ExceptionTest2();
		  test.display(new SubClass());
		  
	}
	
	public void display(SuperClass s)
	{
		try {
			s.method();
		}catch(IOException e) {
			e.printStackTrace();
		}
	}
}

class SuperClass{
	public void method() throws IOException{
		
	}
}

class SubClass extends SuperClass{
	public void method()  throws IOException{
		
	}
}
~~~

手动生成的异常对象，并抛出(throw)

 throw 和 throws的区别
 throw表示抛出一个异常类的对象，生成异常对象的过程，声明在方法体内
 throws属于异常处理的一种方式，声明在方法的声明处

~~~java
 如何自定义异常类
1. 继承于现有的异常类：RuntimeException(可以不用显式处理)、Exception(必须考虑如何显式的处理)
2. 提供全局常量：serialVersionUID 
3. 提供重载的构造器


 *
 */
public class MyException extends RuntimeException {
	//唯一标识定义的类
	static final long serialVersionUID = -70348945766939L; 
	
	
	public MyException() {
		
	}
	
	public MyException(String msg)
	{
		super(msg);
	}
}

public class StudentTest {
	public static void main(String[] args) {
		try {
			Student s = new Student();
			s.regist(-11001);
			System.out.println(s.id);
		} catch (Exception e) {
			// TODO Auto-generated catch block
			//e.printStackTrace();
			System.out.println(e.getMessage());
		}
	}
}

class Student{
	int id;
	//throws处理Exception异常，向上报给try-catch
	public void regist(int id) throws Exception{
		if(id > 0)
		{
			this.id = id;
		}else {
			//手动抛出异常
			//生成一个异常对象
			//运行时异常可以不处理
			//throw new RuntimeException("数据非法!");
			
			//Exception不一定是运行异常，需要处理 
			//throw new Exception("数据非法!");
			throw new MyException("不能输入负数");
		}
		
	}
}
~~~

# 第二部分 Java高级

### 多线程

JVM的内存模型：方法区、堆、虚拟机栈、程序计数器、本地方法栈（暂时忽略）
同一个Java程序的多个线程各自拥有独自的虚拟机栈、程序计数器，多个线程共享方法区和堆

~~~java
/*

多线程的创建，方式一：继承于Thread类
1. 创建一个继承于Thread类的子类
2. 重写Thread类的run()方法 ：将此线程执行的操作声明在run方法中
3. 创建Thread类的子类对象
4. 通过此对象调用start()方法

 */
public class ThreadTest {
    public static void main(String[] args) {
        //3.创建Thread类的子类的对象
        MyThread myThread = new MyThread();
        //4.通过对象调用start()的方法：①启动当前线程 ②调用当前线程的run()方法
        myThread.start();
        //注意1：不能通过直接调用run()方法启动线程
        //myThread.run();

        //注意2：不可以让已经启动的线程再次执行，会报错IllegalThreadStateException
        //myThread.start();
        //需要重写创建一个线程的对象
        MyThread t2 = new MyThread();
        t2.start();
        //如下操作仍然是在main线程中去执行
        System.out.println("hello");

    }

}

//1.创建Thread类的子类
class MyThread extends Thread{
    //重写Thread类中的run方法
    public void run(){
        for(int i = 0; i < 100; i++)
        {
            if(i % 2 == 0){
                System.out.println(i);
            }
        }
    }
}
~~~

~~~java
/*
创建多线程的方式二：实现Runnable接口
1. 创建一个实现了Runnable接口的类
2. 实现类去实现Runnable中的抽象方法：run()
3. 创建实现类的对象
4. 将此对象作为参数传递到Thread类的构造器中，创建Thread类的对象
5. 通过Thread类的对象调用start()

比较创建线程的两种方式：
开发中：优先选择：实现Runnable接口的方式
原因：1、实现的方式没有类的单继承性的局限
     2、实现的方式更适合来处理多个线程共享数据的情况

 联系：public class Thread implements Runnable
相同点 两种方式都需要重写run()，将线程要执行的声明在run()中
* */


public class ThreadTest1 {
    public static void main(String[] args) {
        MThread mThread = new MThread();
        Thread t1 = new Thread(mThread);
        //通过Thread类的对象调用start()作用：①启动线程 ②调用当前线程的run()--->调用了Runnable类型的target的run()
        t1.start();


    }
}

class MThread implements Runnable{

    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            if(i % 2 == 0)
            {
                System.out.println(Thread.currentThread().getName() + ":" + i);
            }
        }
    }
}
~~~

~~~java
/*
*
测试Thread中的常用方法
1.start()：启动当前线程，调用当前线程的run()
2.run():通常需要重写Thread类中的方法，将创建的线程要执行的操作声明在此方法中
3.currentThread():静态方法，返回当前代码的线程
4.getName():获取当前线程的名字
5.setName():设置当前线程的名字
6.yield(): 释放当前cpu的执行权,但是CPU有可能又分配给当前线程
7.join():在线程a中调用线程b的join()，此时调用完线程a进入阻塞状态，直到线程B完全执行完，线程A才结束阻塞状态
8.stop():已过时。当执行此方法时，强制结束当前线程
9.sleep(long millitime):让当前线程“睡眠”指定的毫秒数。在指定的时间之内当前线程是阻塞状态
10.isAlive():

线程的优先级：
1.MAX_PRIORITY:10
2.MIN_PRIORITY:1
NORM_PRIORITY:5 --默认优先级

2.如何获取和设置当前线程的优先级
    getPriority();
     setPriority(int p);
    说明：高优先级的线程要抢占低优先级的线程的CPU，但只是从概率上讲，高优先级的线程高概率的情况下被执行，
    并不意味着只有当高优先级的线程执行以后，低优先级的线程才执行
* */
public class ThreadMethodTest {
    public static void main(String[] args) {
        HelloThread h1 = new HelloThread("线程1");
      //  h1.setName("线程1");
        h1.setPriority(Thread.MAX_PRIORITY);
        h1.start();

        //给主线程命名
        Thread.currentThread().setName("主线程");
        Thread.currentThread().setPriority(Thread.MIN_PRIORITY);
        for (int i = 0; i < 100; i++) {
            if(i % 2 == 0)
            {
                System.out.println(Thread.currentThread().getName() + ":" + Thread.currentThread().getPriority() + ":" + i);
            }
//            if(i == 20)
//            {
//                try {
//                    h1.join();
//                } catch (InterruptedException e) {
//                    e.printStackTrace();
//                }
//            }
        }

        System.out.println(h1.isAlive());
    }
}

class HelloThread extends Thread{
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            if(i % 2 == 0)
            {
//                try {
//                    sleep(10);
//                } catch (InterruptedException e) {
//                    e.printStackTrace();
//                }
                System.out.println(Thread.currentThread().getName() + ":" + +Thread.currentThread().getPriority() + ":" +  i);
            }
//            if(i % 20 == 0)
//            {
//                yield();
//            }
        }
    }

    public HelloThread (String name){
        super(name);
    }
}
~~~

~~~java
public class WindowTest1 {
    public static void main(String[] args) {
        Window w1 = new Window("线程1");
        Window w2 = new Window("线程2");
        Window w3 = new Window("线程3");

        
        w1.start();
        w2.start();
        w3.start();
    }

}

class Window extends Thread{
    private static int ticket = 100;
    public Window(String name){
        super(name);

    }
    public void run(){

        while(ticket >= 0){
            System.out.println(Thread.currentThread().getName()+ ":" + " 当前的票数是：" + ticket);
            ticket--;
        }
    }
}
~~~

~~~java
public class WindowTest2 {
    public static void main(String[] args) {
        Window2 w = new Window2();
        Thread t1 = new Thread(w);
        Thread t2 = new Thread(w);
        Thread t3 = new Thread(w);

        t1.setName("线程1");
        t2.setName("线程2");
        t3.setName("线程3");

        t1.start();
        t2.start();
        t3.start();
    }
}

class Window2 implements Runnable{

    private int ticket = 100;
    @Override
    public void run() {
        while(ticket > 0){
            System.out.println(Thread.currentThread().getName() + "当前票数：" + ticket);
            ticket--;
        }
    }
}
~~~



~~~java
//例子 创建三个窗口卖票，总票为100张，使用实现Runnable接口的方式

/*
*
1.问题：卖票过程中出现重票、错票 -->出现线程安全问题
2.问题出现的原因：当某个线程操作车票的过程中，尚未操作完成，其他线程参与进来操作车票
3.如何解决：当一个线程在操作共享数据的时候，其他线程不能参与进来，直到线程a操作完ticket时，
    其他线程才可以开始操作ticket。这种情况即使线程a出现了阻塞，也不能改变
4.在Java当中，通过同步机制来解决线程安全问题

方式一：同步代码块
    synchronized(同步监视器){
        //需要被同步的代码
    }
    说明：①操作共享数据的代码即需要被同步的代码 --->不能包含代码多了（可能导致只有一个线程执行程序），也不能包含代码少了
         ②同步监视器：即锁 任何一个类的对象都可以充当锁
         ③要求：*多个线程必须共用同一把锁*。

       补充：在实现Runnable接口创建多线程的方式中，可以考虑使用this充当同步监视器
       在继承Thread类创建多线程的方式中，慎用this充当监视器，可以考虑当前类充当监视器

方式二：同步方法
    如果操作共享数据的代码完整的声明在一个方法中，不妨将此方法申明为同步的

5.同步方式，解决了线程的安全问题(好处)
  操作同步代码时，只能有一个线程参与，其他线程等待，相当于是一个单线程的过程，效率低(局限性)



* */
public class WindowTest2 {
    public static void main(String[] args) {
        Window2 w = new Window2();
        Thread t1 = new Thread(w);
        Thread t2 = new Thread(w);
        Thread t3 = new Thread(w);

        t1.setName("线程1");
        t2.setName("线程2");
        t3.setName("线程3");

        t1.start();
        t2.start();
        t3.start();
    }
}

class Window2 implements Runnable{

    private int ticket = 100;
    Object obj = new Object();


    @Override
    public void run() {
//        synchronized (obj){
//            while(ticket > 0){
//                try {
//                    Thread.sleep(100);
//                } catch (InterruptedException e) {
//                    e.printStackTrace();
//                }
//                System.out.println(Thread.currentThread().getName() + "当前票数：" + ticket);
//                ticket--;
//            }
//        }

        while(true){
            synchronized (this){
            if(ticket > 0){
                try {
                    Thread.sleep(100);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                System.out.println(Thread.currentThread().getName() + "当前票数：" + ticket);
                ticket--;
            }else
                break;
        }
        }

    }
}
~~~

~~~java
/*
*

使用同步方法解决实现Runnable接口的线程安全问题

关于同步方法的总结:
1.同步方法仍然涉及到同步监视器，只是不需要显式的声明
2.非静态的同步方法，同步监视器是：this
    静态的同步方法，同步监视器是类的本身


* */
public class WindowTest3 {
    public static void main(String[] args) {
        Window3 w = new Window3();
        Thread t1 = new Thread(w);
        Thread t2 = new Thread(w);
        Thread t3 = new Thread(w);

        t1.setName("线程1");
        t2.setName("线程2");
        t3.setName("线程3");

        t1.start();
        t2.start();
        t3.start();
    }
}

class Window3 implements Runnable{

    private int ticket = 100;
    private static boolean flags = true;

    @Override
    public void run() {
        while(flags){
            show();
        }
    }

    public synchronized void show(){ //同步监视器:this
       // synchronized (this) {
            if(ticket > 0){
                try {
                    Thread.sleep(100);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                System.out.println(Thread.currentThread().getName() + ":" + " 当前剩余的票数:" + ticket);
                ticket--;
            }else if(ticket == 0){
                flags = false;
            }
        //}

    }
}
~~~

~~~java
//使用同步机制将单例模式中的懒汉式改写为线程安全的


public class BankTest {

}

class Bank{
    private Bank(){

    }

    private static Bank bank = null;

    //单例模式中懒汉式是线程不安全的
    //利用线程同步将其改为线程安全
    //方式一 效率较差 原因是当多个线程去访问bank时 都需要经过同步机制
    //当前代码只有第一个线程回去创建Bank()对象，后续的线程只需要直接访问即可
//    public synchronized  static Bank getBank(){
//        if (bank == null) {
//            bank = new Bank();
//        }
//        return bank;
//    }

    //方式二 效率更高
    public static Bank getBank() {
        synchronized (Bank.class) {
            if(bank == null){
                bank = new Bank();
            }
        }
        return bank;
    }
}
~~~

~~~java
/*
*

解决线程安全问题的三个方式：Lock锁 ---JDK5.0新增

1. 面试题：synchronized 和 Lock的异同
    相同点：两者都可以解决线程安全问题
    不同点：synchronized机制在执行完相应的同步代码以后，自动释放同步监视器
    Lock需要手动的启动同步机制(Lock())，同时结束同步也需要手动的实现(unlock())

注意在继承Thread类创建多线程的方式中 需要保证锁是静态的:
private static ReentrantLock lock = new ReentrantLock();

2.优先使用顺序
Lock -> 同步代码块(已经进入方法体，分配相应资源) ->同步方法(在方法体之外)


* */
public class LockTest {

    public static void main(String[] args) {
        Window w = new Window();
        Thread t1 = new Thread(w);
        Thread t2 = new Thread(w);
        Thread t3 = new Thread(w);

        t1.setName("线程1");
        t2.setName("线程2");
        t3.setName("线程3");

        t1.start();
        t2.start();
        t3.start();

    }
}

class Window implements Runnable {

    private int ticket = 100;

    //1.实例化ReentrantLock
    private ReentrantLock lock = new ReentrantLock();


    @Override
    public void run() {
        while(true){
            try{
                //2.调用锁定方法lock(),保证
                lock.lock();
                if (ticket > 0) {
                    try {
                        Thread.sleep(100);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                    System.out.println(Thread.currentThread().getName() + " ：剩余票数为 " + ticket);
                    ticket--;
                }else{
                    break;
                }
            }finally{
                //调用解锁的方法:unlock()
                lock.unlock();
            }

        }
    }
    
}
~~~

~~~java
/*
*

线程通信的例子：使用两个线程打印1-100 线程1 线程2 交替打印

涉及的线程通信的三个方法：
wait():一旦执行此方法，当前线程就进入阻塞状态，并释放同步监视器。
notify():一旦执行此方法，就会唤醒一个被wait()的线程。如果有个线程被wait()，就选择优先级高的那个
notifyAll():一旦执行此方法，就会唤醒所有被wait的线程。


说明：
1.wait(),notify(),notifyAll()三个方法必须使用在同步代码块或同步方法中。
2.wait(),notify(),notifyAll()三个方法的调用者必须是同步代码块或同步方法中的同步监视器
3.wait(),notify(),notifyAll()三个方法是定义在java.lang.Object类中

面试题：sleep() 和 wait()的异同？
1.相同点：一旦执行方法，都可以使得当前线程进入阻塞状态
2.不同点：1）两个方法声明的位置就不一样：Thread类中声明sleep()，Object类中声明wait()
         2）调用的范围不同：sleep()可以在任何需要的场景下调用，而wait()必须使用在同步代码块或同步方法中。
        3）关于是否释放同步监视器：如果两个方法都使用在同步代码块中或同步方法中，sleep()不会释放锁，
        wait()会释放锁


*/
public class CommunicationTest {
    public static void main(String[] args) {
        Number n = new Number();
        Thread t1 = new Thread(n);
        Thread t2 = new Thread(n);

        t1.setName("线程1");
        t2.setName("线程2");

        t1.start();
        t2.start();
    }
}

class Number implements Runnable{

    private int number = 0;

    @Override
    public void run() {
        while (true) {
            synchronized (this){
                //唤醒被阻塞的线程，但此时进入同步代码块的线程拥有锁，被唤醒的线程进不来
                notify();
                if (number <= 100) {
                    try {
                        Thread.sleep(10);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                    System.out.println(Thread.currentThread().getName() + ":" + number);
                    number++;


                    //使得调用如下wait()方法的线程进入阻塞状态
                    try {
                        //线程一旦执行wait()操作会释放锁给其他线程
                        wait();
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                } else {
                    break;
                }
            }
        }
    }


}
~~~

### String字符串

~~~java
/*

String:字符串,使用一对""引起来表示
1. String声明为final的，不可以被继承。
2. String实现了Serializable接口: 表示字符串是支持序列化的
          实现了Comparable接口: 表示String可以比较大小
3. String内部定义了final char[] value用于存储字符串序列
4. String:代表不可变的字符序列。（不可变性）
    体现：1.当对字符串重新赋值时，需要重新指定内存区域，不能使用原先存在的value数组进行赋值，因为value数组是final类型的
         2.对现有的字符串进行连接操作时，也需要重新指定内存区域，不能使用原有的value数组进行赋值
         3.当调用String的replace()方法修改指定的字符或者字符串时，也需要重新指定内存区域，不能使用原有的value数组进行赋值。
5. 通过字面量的方式（区别于new）方式给一个字符串赋值，此时的字符串值声明在字符串常量池中，该字符串的地址赋给了String类型对象
6. 字符串常量池中是不会存储相同内容的字符串的

String的实例化方式
方式一：通过字面量定义的方式
方式二：通过new + 构造器的方式

面试题：String s = new String("abc"); 以该方式创建对象，在内存中创建了多少个对象？
    两个：一个是堆空间中new结构，另一个是char[]对应的常量池中的数据：“abc”


结论：
1.常量于常量的拼接结果在常量池，且常量池中不存在相同内容的常量
2.拼接中只要其中有一个是变量，结果就在堆中
*/
public class StringTest {

    @Test
    public void test1(){
        String s1 = "abc"; //字面量的定义方式
        String s2 = "abc";
        //s1 = "hello";

        System.out.println(s1 == s2);  //两个对象比较的是地址值
        System.out.println(s1); //hello
        System.out.println(s2); //abc
        System.out.println("*********************************");

        //s2和s3定义了相同内容的字面量。因此s2,s3的地址值相同
        String s3 = "abc";
        s3 += "def";
        System.out.println(s3);
        System.out.println(s2);
        System.out.println("*********************************");

        String s4 = "abc";
        String s5 = s4.replace('a', 'b');
        System.out.println(s5);
    }
    运行结果：
true
abc
abc
*********************************
abcdef
abc
*********************************
bbc





    @Test
    public void test2(){
        //通过字面量定义的方式:此时的s1和s2的数据JavaEE声明在方法区中的字符串常量池中
        String s1 = "javaEE";
        String s2 = "javaEE";

        //通过new + 构造器的方式：此时的s3和s4保存的地址值，是数据在堆空间中开辟空间
        String s3 = new String("javaEE");
        String s4 = new String("javaEE");

        System.out.println(s1 == s2); //true
        System.out.println(s1 == s3); //false
        System.out.println(s1 == s4); //false
        System.out.println(s3 == s4); //false
        System.out.println("*******************************");

        Person p1 = new Person("javaEE", 10);
        Person p2 = new Person("javaEE", 10);

        //通过字面量方式定义
        System.out.println(p1.name = p2.name);

    }
 运行结果：
 true
false
false
false
*******************************
javaEE

//结论：
//1.常量与常量的拼接结果在常量池，且常量池中不存在相同内容的常量
//2.拼接中只要其中有一个是变量，结果就在堆中
// 3.如果拼接的结果调用intern()方法，返回值就在常量池中
    @Test
    public void test3(){
        String s1 = "javaEE";
        String s2 = "hadoop";

        String s3 = "javaEEhadoop";
        String s4 = "javaEE" + "hadoop";
        String s5 = s1 + "hadoop";
        String s6 = "javaEE" + s2;
        String s7 = s1 + s2;

        System.out.println(s3 == s4); //true
        System.out.println(s3 == s5); //false
        System.out.println(s3 == s6); //false
        System.out.println(s3 == s7); //false
        System.out.println(s5 == s6); //false
        System.out.println(s5 == s7); //false
        System.out.println(s6 == s7); //false

        String s8 = s5.intern(); //返回值得到的s8使用的是常量池中已经存在的“javaEEhadoop”
        System.out.println(s3 == s8);//true



    }

    @Test
    public void test4(){
        String s1 = new String("good");
        String s2 = s1;
        s2 = "nihao";
        System.out.println(s1); //good
    }

}

class Person{
     public  String name;
    public int age;

    public Person() {
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
~~~

~~~java
/*
*
int length()：返回字符串的长度： return value.length
char charAt(int index)： 返回某索引处的字符return value[index]
boolean isEmpty()：判断是否是空字符串：return value.length == 0
String toLowerCase()：使用默认语言环境，将 String 中的所有字符转换为小写
String toUpperCase()：使用默认语言环境，将 String 中的所有字符转换为大写
String trim()：返回字符串的副本，忽略前导空白和尾部空白
boolean equals(Object obj)：比较字符串的内容是否相同
boolean equalsIgnoreCase(String anotherString)：与equals方法类似，忽略大
小写
String concat(String str)：将指定字符串连接到此字符串的结尾。 等价于用“+”
int compareTo(String anotherString)：比较两个字符串的大小
String substring(int beginIndex)：返回一个新的字符串，它是此字符串的从beginIndex开始截取到最后的一个子字符串。
String substring(int beginIndex, int endIndex) ：返回一个新字符串，它是此字符串从beginIndex开始截取到endIndex(不包含)的一个子字符串。


* */


import org.junit.Test;

public class StringMethod {
    @Test
    public void test1() {
        String s1 = "Hello world";
        System.out.println(s1.length());

        System.out.println(s1.charAt(0));
        System.out.println(s1.charAt(9));
     //   System.out.println(s1.charAt(10));
    //    s1 = "";
        System.out.println(s1.isEmpty());
        String s2 = s1.toLowerCase();
        System.out.println(s1); //s1不可变，仍然为原来的字符串
        System.out.println(s2);

        String s3 = "   he llo world   ";
        String s4 = s3.trim();
        System.out.println(s3);
        System.out.println(s4);


    }

    @Test
    public void test2(){
        String s1 = "helloworld";
        String s2 = "HelloWorld";

        System.out.println(s1.equals(s2));
        System.out.println(s1.equalsIgnoreCase(s2));

        String s3 = "abc";
        String s4 = s3.concat("def");
        System.out.println(s4);

        String s5 = "abc";
        String s6 = new String("abe");
        System.out.println(s5.compareTo(s6));

        String s7 = s1.substring(5);
        System.out.println(s7);

        String s8 = s1.substring(0,5);
        System.out.println(s8);
    }
}
~~~

~~~java
public class StringTest1 {
    /*
    复习：
        String与基本数据类型、包装类之间的转换

        String-->基本数据类型、包装类：调用包装类的静态方法：parseXxx(str)
        基本数据类型、包装类 -->String：调用String重载的Valueof(Xxx)
    */

    @Test
    public void test1(){
        String s1 =  "123";
        int num = Integer.parseInt(s1);

        String s2 = String.valueOf(num);
        String s3 = num + "";
        System.out.println(s1 == s3);

    }

    /*
    String 与 char[]之间的转换
    String --> char[]:调用String的toCharArray()
    char[] --> String:调用String的构造器
    */
    @Test
    public void test2(){
        String str1 = "abc123";
        char[] charArray = str1.toCharArray();
        for (int i = 0; i < charArray.length; i++) {
            System.out.println(charArray[i]);
        }

        char[] arr = new char[]{'h', 'e', 'l', 'l', 'o'};
        String str2 = new String(arr);
        System.out.println(str2);

    }

    /*

    String 与 byte[]之间的转换
    编码：String -->byte[]:调用String的getBytes()
    解码：byte[] -->String:调用String的构造器

    //编码：字符串--->字节（看得懂--->看不懂的二进制数据）
    //解码：编码的逆过程，字节--->字符串（看不懂的二进制数据---> 看得懂）

    //说明：解码时要求解码使用的字符集必须与编码时使用的字符集一致，否则会出现乱码。
    */
    @Test
    public void Test3(){
    String str1 = "abc123";
    byte[] bytes = str1.getBytes();//使用默认字符集进行编码
    System.out.println(Arrays.toString(bytes));
    //运行结果：[97, 98, 99, 49, 50, 51]

    String str2 = new String(bytes);
    System.out.println(str2);
    }
}

~~~

~~~java
例题
public class Test1 {
    String str = new String("good");
    char[] ch = {'t', 'e', 's', 't'};

    //引用数据类型传的是地址值，而基本数据类型是值传递
    //但是注意：不是传了地址值，方法里面修改了，导致原来的实参的值也变（错误！！！）
    //String类型是引用数据类型，但由于不可变性，重新赋值需要重新指定内存区域
    public void change(String str, char ch[]) {
        str = "test ok";
        ch[0]  = 'b';
    }

    public static void main(String[] args) {
        Test1 t = new Test1();
        t.change(t.str, t.ch);
        System.out.println(t.str); //good
        System.out.println(t.ch); //best

    }
}
~~~



StringBufferBuilder

~~~JAVA
/*

关于StringBuffer和StringBuilder的使用
String:不可变的字符序列
StringBuffer:可变的字符序列;线程安全的，效率低；底层使用char[]存储
StringBuilder:可变的字符序列;jdk5.0新增的，线程不安全，效率高；底层使用char[]存储

源码分析：
String str = new String(); //char[] value = new char[0]
String str1 = new String("abc"); //char[] value = new char[]{'a', 'b', 'c'};

StringBuffer sb1 = new StringBuffer();//char[] value = new char[16]; 底层创建了一个长度为16的数组
System.out.println(sb1.length()); //长度实际是0，求的是字符串实际个数
sb1.append('a'); //value[0] = 'a';
sb1.append('b'); //value[1] = 'b';
StringBuffer sb2 = new StringBuffer("abc"); //char[] value = new char["abc".length() + 16];

//问题1 System.out.println(sb2.length()); //3
//问题2 扩容问题：如果要添加的数据底层数组容不下了，那就需要扩容底层的数组
        默认情况下，扩容为原来的2倍+2，同时将原有数组的元素复制到新的数组中。

        指导意义：开发中建议使用StringBuffer(int capacity) 或 StringBuilder(int capacity)


StringBuffer append(xxx)：提供了很多的append()方法，用于进行字符串拼接
StringBuffer delete(int start,int end)：删除指定位置的内容
StringBuffer replace(int start, int end, String str)：把[start,end)位置替换为str
StringBuffer insert(int offset, xxx)：在指定位置插入xxx
StringBuffer reverse() ：把当前字符序列逆转
public int indexOf(String str)
public String substring(int start,int end)//返回一个从start开始到end索引结束的左闭右开的子字符串
public int length()
public char charAt(int n )
public void setCharAt(int n ,char ch)

    总结：增：append(xxx)
        删：delete(int start, int end)
        改：setCharAt(int n, char ch) / replace(int start, int end, String str)
        查：charAt(int n)
        插：insert(int offset, xxx)
        长度：length();
        遍历：for() + charAt() / toString()

对比String、StringBuffer、StringBuilder三者的效率：
从高到低：StringBuilder > StringBuffer > String 

String与StringBuffer、StringBuilder之间的转换
String-->StringBuffer、StringBuilder:调用StringBuffer、StringBuilder构造器
StringBuffer、StringBuilder-->String:①调用String构造器；
                                    ②StringBuffer、StringBuilder的toString()方法
 */
public class StringBufferBuilder {

    @Test
    public void test1(){
        StringBuffer s1 = new StringBuffer("abc");
        s1.append(1);
        s1.append('1');
        System.out.println(s1);

        // s1.delete(2,4);
       // s1.replace(2, 4, "hello");
      //  s1.insert(2, "false");
        String s2 = s1.substring(2, 4);
        System.out.println(s2);
        System.out.println(s1);
        System.out.println(s1.length());

    }

}
~~~

~~~JAVA

/*

JDK 8之前日期和时间的API测试

 */
public class DateTimeTest {
    //1.System类中的currentTimeMillis()
    @Test
    public void test1(){
        long time = System.currentTimeMillis();
        //返回当前时间与1970年1月1日0时0分0秒之间以毫秒为单位的时间差
        //称为时间戳
        System.out.println(time);
    }


    /*
       java.util.Date类
                |---java.sql.Date类 （父、子类关系 ）
    1.两个构造器的使用
        ①构造器一：Date() : 创建一个对应当前时间的Date对象
        ②构造器二：创建指定毫秒数的Date对象

    2.两个方法的使用
        ①toString():显式当前的年、月、日、时、分、秒
        ②getTime():获取当前Date对象对应的毫秒数。（时间戳）

     3.java.sql.Date:对应数据库中的日期类型的变量
            ①如何实例化
            ②如何将java.util.Date对象转换为sql.Date对象
    */
    @Test
    public void test2(){
        //构造器一：Date() ：创建一个对应当前时间的Date对象
        Date date1 = new Date();
        System.out.println(date1.toString()); //Wed Aug 18 08:46:16 CST 2021
        System.out.println(date1.getTime());  //1629247965409

        //构造器二：创建指定毫秒数的Date对象
        Date date2 = new Date(1629247965409L);
        System.out.println(date2.toString());

        //创建java.sql.Date对象
        java.sql.Date date3 = new java.sql.Date(1629247965409L);
        System.out.println(date3);

        //如何将java.util.Date对象转换为sql.Date对象
        //情况一
        //Date date4 = new java.sql.Date(1629247965409L);
        //java.sql.Date date5 = (java.sql.Date) date4;
        //情况二
        Date date6 = new Date();
        java.sql.Date date7 = new java.sql.Date(date6.getTime());

    }



}
~~~



~~~JAVA
/*
一、说明：Java中的对象，正常情况下，只能进行比较：== 或 ！= 不能使用 > 或 < 的
        但是开发场景中，需要对多个对象进行排序，言外之意，就需要比较对象的大小。
        如何实现？使用两个接口中的任何一个：Comparable 或 Comparator

二、Comparable接口的使用
1.像String、包装类等实现Comparable接口，重写了compareTo(Obj)方法，给出了比较两个对象大小
2.像String、包装类重写compareTo()方法以后，进行了从小到大的排列
3.重写compareTo(obj)的规则：
    如果当前对象this大于形参对象obj,则返回正整数
    如果当前对象this小于形参对象obj,则返回负整数
    如果当前对象this等于形参对象obj，则返回零
4.对于自定义类来说，如果需要排序，我们可以让自定义类实现Comparable接口，
    重写compareTo(Obj)方法中指明如何排序


 */
public class CompareTest {
   @Test
   public void test01(){
       String[] arr = new String[]{"AA", "CC", "KK", "MM", "GG", "JJ", "DD"};
       Arrays.sort(arr);
       System.out.println(Arrays.toString(arr));
   }

   @Test
    public void test02(){
       Goods[] arr = new Goods[4];
       arr[0] = new Goods("lenovo", 1000);
       arr[1] = new Goods("dell", 500);
       arr[2] = new Goods("xiaomi", 200);
       arr[3] = new Goods("huawei", 1500);
       Arrays.sort(arr);
       System.out.println(Arrays.toString(arr));
   }

   /*
   Comparator接口的使用：定制排序
   1.背景：
   当元素的类型没有实现java.lang.Comparable接口而又不方便修改代码，
   或者实现Java。lang.Comparable接口的排序规则而又不适合当前的操作，
   那么可以考虑使用Comparator的对象来排序。

   2.重写compare(Object o1, Object o2)方法，比较o1和o2的大小；
        如果方法返回正整数，则表示o1大于o2；
        如果返回0则表示相等；
        返回负整数，表示o1小于o2
    */

    @Test
    public void test3(){
        String[] arr = new String[]{"AA", "CC", "KK", "MM", "GG", "JJ", "DD"};
        Arrays.sort(arr, new Comparator(){

            //按照字符串从小到大的顺序排列
            @Override
            public int compare(Object o1, Object o2) {
                if(o1 instanceof String && o2 instanceof String){
                    String s1 = (String)o1;
                    String s2 = (String)o2;
                    return -s1.compareTo(s2);
                }
                throw new RuntimeException("输入的数据类型不一致");
            }
        });
        System.out.println(Arrays.toString(arr));
    }

    @Test
    public void test4(){
        Goods[] arr = new Goods[4];
        arr[0] = new Goods("lenovo", 1000);
        arr[1] = new Goods("dell", 500);
        arr[2] = new Goods("xiaomi", 200);
        arr[3] = new Goods("huawei", 1500);

        Arrays.sort(arr);
        System.out.println(Arrays.toString(arr));
    }

}


public class Goods implements Comparable {
    private String name;
    private double price;

    public Goods() {
    }

    public Goods(String name, double price) {
        this.name = name;
        this.price = price;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public double getPrice() {
        return price;
    }

    public void setPrice(double price) {
        this.price = price;
    }


    public String toString() {
        return "Goods{" + "name:" + name + " ,price:" + price + "}";
    }
    //指明商品比较大小的方式
    @Override
    public int compareTo(Object o) {
        if (o instanceof Goods) {
            Goods good = (Goods) o;
            //方式一：
            if (this.price > good.price) {
                return 1;
            } else if (this.price < good.price) {
                return -1;
            } else if (this.price == good.price) {
                return 0;
            }
        }

        throw new RuntimeException("传入的数据类型不一致！");

    }


}
~~~



~~~java
/*
一、说明：Java中的对象，正常情况下，只能进行比较：== 或 ！= 不能使用 > 或 < 的
        但是开发场景中，需要对多个对象进行排序，言外之意，就需要比较对象的大小。
        如何实现？使用两个接口中的任何一个：Comparable 或 Comparator

二、Comparable接口与comparator的使用对比
Comparable接口的方式一旦确定，保证Comparable接口实现类的对象在任何位置都可以比较大小
Comparator接口属于临时性比较

二、Comparable接口的使用
1.像String、包装类等实现Comparable接口，重写了compareTo(Obj)方法，给出了比较两个对象大小
2.像String、包装类重写compareTo()方法以后，进行了从小到大的排列
3.重写compareTo(obj)的规则：
    如果当前对象this大于形参对象obj,则返回正整数
    如果当前对象this小于形参对象obj,则返回负整数
    如果当前对象this等于形参对象obj，则返回零
4.对于自定义类来说，如果需要排序，我们可以让自定义类实现Comparable接口，
    重写compareTo(Obj)方法中指明如何排序


 */
public class CompareTest {
   @Test
   public void test01(){
       String[] arr = new String[]{"AA", "CC", "KK", "MM", "GG", "JJ", "DD"};
       Arrays.sort(arr);
       System.out.println(Arrays.toString(arr));
   }

   @Test
    public void test02(){
       Goods[] arr = new Goods[4];
       arr[0] = new Goods("lenovo", 1000);
       arr[1] = new Goods("dell", 500);
       arr[2] = new Goods("xiaomi", 200);
       arr[3] = new Goods("huawei", 1500);
       Arrays.sort(arr);
       System.out.println(Arrays.toString(arr));
   }

   /*
   Comparator接口的使用：定制排序
   1.背景：
   当元素的类型没有实现java.lang.Comparable接口而又不方便修改代码，
   或者实现Java。lang.Comparable接口的排序规则而又不适合当前的操作，
   那么可以考虑使用Comparator的对象来排序。

   2.重写compare(Object o1, Object o2)方法，比较o1和o2的大小；
        如果方法返回正整数，则表示o1大于o2；
        如果返回0则表示相等；
        返回负整数，表示o1小于o2
    */

    @Test
    public void test3(){
        String[] arr = new String[]{"AA", "CC", "KK", "MM", "GG", "JJ", "DD"};
        Arrays.sort(arr, new Comparator(){

            //按照字符串从小到大的顺序排列
            @Override
            public int compare(Object o1, Object o2) {
                if(o1 instanceof String && o2 instanceof String){
                    String s1 = (String)o1;
                    String s2 = (String)o2;
                    return -s1.compareTo(s2);
                }
                throw new RuntimeException("输入的数据类型不一致");
            }
        });
        System.out.println(Arrays.toString(arr));
    }

    @Test
    public void test4(){
        Goods[] arr = new Goods[4];
        arr[0] = new Goods("lenovo", 1000);
        arr[1] = new Goods("dell", 500);
        arr[2] = new Goods("xiaomi", 200);
        arr[3] = new Goods("huawei", 1500);

        Arrays.sort(arr);
        System.out.println(Arrays.toString(arr));
    }

}

~~~

