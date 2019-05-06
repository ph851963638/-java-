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
抽象类中可以定义属性、方法、构造方法，接口中只能定义方法和返回类型，无法定义属性和构造器；
1.抽象类可以有默认的实现完全是抽象的，接口不存在方法的实现；
2.抽象类使用extends关键字来继承抽象类；子类使用implements实现接口。
3.抽象方法可以有public 、protected 和default的修饰符。接口默认使用修饰符public，不能用其他修饰符。
4.抽象类在java语言中所表示的是一种继承关系，一个子类只能存在一个父类，但是可以存在多个接口。抽象类是单继承，接口实现多继承。
5.抽象方法比接口速度快
十五、java 中 IO 流分为几种？
第一, 输入流,输出流 .
第二, 字节流,字符流 . 
第三, 节点流(真正直接处理数据的) ,处理流(装饰加工节点流的) 
十六、BIO、NIO、AIO 有什么区别？
BIO(阻塞 I/O), 
NIO(非阻塞 I/O), 
AIO (异步 I/O),
BIO方式适用于连接数目比较小且固定的架构，这种方式对服务器资源要求比较高，并发局限于应用中，JDK1.4以前的唯一选择，但程序直观简单易理解。

NIO方式适用于连接数目多且连接比较短（轻操作）的架构，比如聊天服务器，并发局限于应用中，编程比较复杂，JDK1.4开始支持。

AIO方式使用于连接数目多且连接比较长（重操作）的架构，比如相册服务器，充分调用OS参与并发操作，编程比较复杂，JDK7开始支持。

    BIO整个过程都等待返回, NIO和IO多路复用在第二个阶段等待返回, 因此从整个过程来看, 这三个模式都属于同步方式. AIO在整个过程中没有等待返回, 属于异步方式.
    
    
十七、Files的常用方法都有哪些？
jdk提供了一个类，封装了一个路径，提供了一系列方法用于擦欧洲哦该路径所指向的文件。

File(String pathname)	 通过指定的一个字符串类型的文件路径来创建一个新的File对象


File(String parent , String child)	 根据指定的一个字符串类型的父路径和一个字符串类型的子路径
                                      （包括文件名称）创建一个File对象

File(File parent , String child)	  根据指定的 File 类的父路径和字符串类型的子路径
                                   （包括文件名称）创建一个File对象
                                   
boolean  exists();            查看目录是否存在
boolean  delete();            删除是否成功
boolean  createNewFile()      当file对应的文件不存在时， 创建新的文件，  创建成功true 
boolean  getName              返回表示的文件或文件夹的名称
boolean  getPath              返回File对象对应的路径
boolean  getParent()          返回File对象对应目录的父目录，（即返回的目录不包含最后一级子目录） 
boolean  boolean canWrite()   判断File对象对应的文件或者目录是否可写。若可写则返回true，反之返回false 
boolean isFile()              判断File对象对应的是否是文件（不是目录）
boolean isDirectory()	      判断File对象对应的是否是目录（不是文件）
 boolean isAbsolute()	      判断File对象对应的文件或者目录是否是绝对路径
long lastModified()	         返回1970 年1 月1 日 0 时0 分 0 秒到文件最好修改时间的毫秒值
long length()	               返回文件内容长度
String [ ]list()	            返回指定目录的全部内容，只列出名称
File[ ] listFiles()	         返回一个包含了File对象所有子文件和子目录的File数组
 
 
 





 
