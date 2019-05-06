# -java-
自我学习中.......
一、JDK和JRE的区别?
JDK（Java开发工具包）是java环境的核心组件，提供编译，调试和运行一个java程序的工具，可执行文件和二进制文件。
JRE是jvm的实施实现，提供饿了java程序的平台，jre包含了jvm,java二进制文件。执行java程序只需要安装jre即可；不需要jdk;
jdk是用于开发jre用于运行；
Java运行时环境(JRE)是将要执行Java程序的Java虚拟机。它同时也包含了执行applet需要的浏览器插件。Java开发工具包(JDK)是完整的Java软件开发包，包含了JRE，编译器和其他的工具(比如：JavaDoc，Java调试器)，可以让开发者开发、编译、执行Java应用程序。
二、== 和 equals 的区别是什么？
1.功能不同  如果两个对象的引用完全相同（指向同一个对象）时，“==”操作将返回true，否则返回false。
==     判断两个对象是否为同一个内存空间；
equals  判断两个变量或者实例指向内存空间的值是否相等；
2.定义不同  == 为运算符号，equals为方法
其主要的不同是一个是操作符一个是方法，==用于对比原生类型  而equals()方法比较对象的相等性。
三、两个对象的 hashCode()相同，则 equals()也一定为 true，对吗？ 不对
   1.相等（相同）的对象必须具有相等的哈希码（或者散列码）。
  2.如果两个对象的hashCode相同，它们并不一定相同。
  *If two objects are equal according to the equals(Object) method, then calling the hashCode method on each of the two      objects must produce the same integer result.
  *It is not required that if two objects are unequal according to the equals(java.lang.Object) method, then calling the    hashCode method on each of the two objects must produce distinct integer results. However, the programmer should be      aware that producing distinct integer results for unequal objects may improve the performance of hash tables.
  关于第一点，相等（相同）的对象必须具有相等的哈希码（或者散列码），为什么？
  因为两个相同的对象 如果当中的哈希码不同，A和B的哈希码不同，则A和B存入HashMap时的哈希码计算得到的HashMap内部数组位置索引可能不同，   那么A和B很有可能允许同时存入HashMap，显然相等/相同的元素是不允许同时存入HashMap。避免重复
　1.如果两个对象相同，那么它们的hashCode值一定要相同；
  2.如果两个对象的hashCode相同，它们并不一定相同（这里说的对象相同指的是用eqauls方法比较）。  
  如不按要求去做了，会发现相同的对象可以出现在Set集合中，同时，增加新元素的效率会大大下降。
  3.equals()相等的两个对象，hashcode()一定相等；equals()不相等的两个对象，却并不能证明他们的hashcode()不相等。
四、final 在 java 中有什么作用？
   1.final关键字 修饰类  方法 域 方法参数  并且final关键字不能被改变
   2.检查final的类不能拥有子类，无法重写
   3.final成员变量必须在声明的时候初始化或者在构造器中初始化，否则就会报编译错误。
   4.被final修饰的变量的引用不可以被改变，引用指向的变量可以被改变；
   5.被final修饰的方法，JVM会尝试为之寻求内联，这对于提升Java的效率是非常重要的
五、java 中的 Math.round(-1.5) 等于多少？
   答：为-1 参数加0.5  向下取整  
   当有效位数确定后，其后面多余的数字应该舍去，只保留有效数字最末一位，这种修约（舍入）规则是“四舍六入五成双”，也即“4舍6入5凑偶”这里“四”是指≤4 时舍去，”六”是指≥6时进上，”五”指的是根据5后面的数字来定，当5后有数时，舍5入1；当5后无有效数字时，需要分两种情况来讲：①5前为奇数，舍5入1；②5前为偶数，舍5不进。（0是偶数）

 六、String 属于基础的数据类型吗？
 不属于    short  void long int double boolean float char byte
 
 七、java 中操作字符串都有哪些类？它们之间有什么区别？
 String、StringBuffer和StringBuilder
String：字符串常量。也就是说String是不可变的对象，因此每次对String类型的对象进行更改操作时，实际上是生成了新的String对象，然后修改指针指向新的String对象。因此可以发现，如果经常要改变字符串内容，用String就会造成内存中大量无引用的对象，当内存不足时GC工作就会引起性能下降
---------------------  速度最慢   
StringBuffer：字符串变量、线程安全；速度一般
StringBuilder:字符串变量、非线程安全；速度最快
八、reverses的方法

   public static String reverse3(String s) {  
        char[] array = s.toCharArray();  
        String reverse = "";  
        for (int i = array.length - 1; i >= 0; i--) {  
            reverse += array[i];  
        }  
        return reverse;  
    }  
    
    public static String reverse4(String s) {  
        return new StringBuilder(s).reverse().toString();  
    }  
 
 
 九、String 类的常用方法都有那些？
   1.toCharArray   字符串变为字符数组
   2.charAt        从字符串中  取出指定位置的字符
   3.substring      字符截取  从一个字符串中取出里面的部分内容
   public String(int beginIndex, int endIndex);
   4. 大小写转换
   public String   toLowerCase(); 大变小
   public String   toUpperCase();  小变大
   
十、抽象类必须要有抽象方法吗？
   答： 抽象类中不一定必须有抽象方法，但若是有抽象方法，类必须是抽象类
   
   
 十一、抽象类和普通类的区别
 1.抽象方法必须为public 或者protected   
 2.抽象类不能用来创建对象 不能被实例化
 3.如果一个类继承于一个抽象类，则子类必须实现父类的抽象方法，如子类没有继承父类的抽象方法，则子类也定义为abstract类。

 
 十二、抽象类能使用 final 修饰吗？
 不能，因为抽象类就是用来继承的，而被final修饰的类不能被继承。
 
 
十三、接口和抽象类有什么区别？
接口中只能定义方法和返回类型，无法定义属性，抽象类可以


 
 
 
 
 
 





 
