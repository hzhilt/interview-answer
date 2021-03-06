* java中==和equals和hashCode的区别

"==" 通常用于基础类型，对比数是否相等，对于引用类型 == 表示两个引用的对象是否是同一个，equals则表示引用的对象是否等价。

* int、char、long各占多少字节数

4 1 8

* int与integer的区别

int 是基本类型 Integer是包装类型 基本类型和包装类型可相互转化
包装类型可以用在list map 这种需要引用类型的方法中
某些方法需要object
integer 可以把 int 转成其他基本类型

* 探探对java多态的理解

从字面去理解就是一个对象可以有多种状态，通过继承和重载来实现多态

多态的父类对象引用变量指向子类对象，通过编译时或者运行时确定操作的行为。

当超类对象引用变量引用子类对象时，被引用对象的类型而不是引用变量的类型决定了调用谁的成员方法，但是这个被调用的方法必须是在超类中定义过的，也就是说被子类覆盖的方法，但是它仍然要根据继承链中方法调用的优先级来确认方法，该优先级为：this.show(O)、super.show(O)、this.show((super)O)、super.show((super)O)。

https://www.cnblogs.com/chenssy/p/3372798.html


* String、StringBuffer、StringBuilder区别

String 不可变，线程安全

StringBuffer 可变，线程安全 append ，insert

StringBuilder 可变，速度更快，非线程安全



* 什么是内部类？内部类的作用

内部类 ： 将一个类的定义在另外一个类的定义内部

每个内部类都能独立地继承一个（接口的）实现，所以无论外围类是否已经继承了某个（接口的）实现，对于内部类都没有影响。

可以利用内部类提供的、可以继承多个具体的或者抽象的类的能力来解决这些程序设计问题。可以这样说，接口只是解决了部分问题，而内部类使得多重继承的解决方案变得更加完整。

	1、内部类可以用多个实例，每个实例都有自己的状态信息，并且与其他外围对象的信息相互独立。

    2、在单个外围类中，可以让多个内部类以不同的方式实现同一个接口，或者继承同一个类。

    3、创建内部类对象的时刻并不依赖于外围类对象的创建。

    4、内部类并没有令人迷惑的“is-a”关系，他就是一个独立的实体。

    5、内部类提供了更好的封装，除了该外围类，其他类都不能访问。
    
https://www.cnblogs.com/chenssy/p/3388487.html

* 抽象类和接口区别

抽象类 最少需要一个抽象方法，可以包含实现方法

接口只定义了方法，不可增加实现

接口中没有构造方式（因为接口不是类）

接口中的方法必须是抽象的（不能实现）

接口中除了static、final变量，不能有其他变量

接口支持多继承（一个类可以实现多个接口）


抽象类可以有默认的方法实现完全是抽象的。接口根本不存在方法的实现

实现 抽象类使用extends关键字来继承抽象类。如果子类不是抽象类的话，它需要提供抽象类中所有声明的方法的实现。子类使用关键字implements来实现接口。它需要提供接口中所有声明的方法的实现。

抽象类可以有构造器，而接口不能有构造器


抽象方法可以有public、protected和default这些修饰符 
接口方法默认修饰符是public。你不可以使用其它修饰符。

抽象类在java语言中所表示的是一种继承关系，一个子类只能存在一个父类，但是可以存在多个接口。

抽象方法比接口速度要快
接口是稍微有点慢的，因为它需要时间去寻找在类中实现的方法。


如果你往抽象类中添加新的方法，你可以给它提供默认的实现。因此你不需要改变你现在的代码。 如果你往接口中添加方法，那么你必须改变实现该接口的类。

* 抽象类的意义

指示了继承者某些必要的行为
指示了不同类型的相同的操作规范

在面向对象方法中，抽象类主要用来进行类型隐藏。构造出一个固定的一组行为的抽象描述，但是这组行为却能够有任意个可能的具体实现方式。

通过从这个抽象体派生，也可扩展此模块的行为功能。

抽象类往往用来表征对问题领域进行分析、设计中得出的抽象概念，是对一系列看上去不同，但是本质上相同的具体概念的抽象。

抽象类的意义：
1，为子类提供一个公共的类型；
2，封装子类中重复内容（成员变量和方法）；
3，定义有抽象方法，子类虽然有不同的实现，但该方法的定义是一致的。

* 抽象类与接口的应用场景

1、interface的应用场合
     A. 类与类之前需要特定的接口进行协调，而不在乎其如何实现。
     B. 作为能够实现特定功能的标识存在，也可以是什么接口方法都没有的纯粹标识。
     C. 需要将一组类视为单一的类，而调用者只通过接口来与这组类发生联系。
     D. 需要实现特定的多项功能，而这些功能之间可能完全没有任何联系。

2、abstract class的应用场合
      一句话，在既需要统一的接口，又需要实例变量或缺省的方法的情况下，就可以使用它。最常见的有：
      A. 定义了一组接口，但又不想强迫每个实现类都必须实现所有的接口。可以用abstract class定义一组方法体，甚至可以是空方法体，然后由子类选择自己所感兴趣的方法来覆盖。
      B. 某些场合下，只靠纯粹的接口不能满足类与类之间的协调，还必需类中表示状态的变量来区别不同的关系。abstract的中介作用可以很好地满足这一点。
      C. 规范了一组相互协调的方法，其中一些方法是共同的，与状态无关的，可以共享的，无需子类分别实现；而另一些方法却需要各个子类根据自己特定的状态来实现特定的功能



* 抽象类是否可以没有方法和属性？

可以

* 接口的意义

组合不同的行为逻辑
规范实现者的行为，可以快速的了解实现者的行为逻辑



* 泛型中extends和super的区别

<? extends T>限定参数类型的上界：参数类型必须是T或T的子类型

<? super T> 限定参数类型的下界：参数类型必须是T或T的超类型


* 父类的静态方法能否被子类重写

不能
静态方法编译期放在内存中，一直存在

* 进程和线程的区别


* final，finally，finalize的区别


Final用于修饰类、成员变量和成员方法。final修饰的类，不能被继承（String、StringBuilder、StringBuffer、Math，不可变类），其中所有的方法都不能被重写，所以不能同时用abstract和final修饰类（abstract修饰的类是抽象类，抽象类是用于被子类继承的，和final起相反的作用）；Final修饰的方法不能被重写，但是子类可以用父类中final修饰的方法；Final修饰的成员变量是不可变的，如果成员变量是基本数据类型，初始化之后成员变量的值不能被改变，如果成员变量是引用类型，那么它只能指向初始化时指向的那个对象，不能再指向别的对象，但是对象当中的内容是允许改变的。

Finally通常和try catch搭配使用，保证不管有没有发生异常，资源都能够被释放（释放连接、关闭IO流）。

Finalize是object类中的一个方法，子类可以重写finalize()方法实现对资源的回收。垃圾回收只负责回收内存，并不负责资源的回收，资源回收要由程序员完成，Java虚拟机在垃圾回收之前会先调用垃圾对象的finalize方法用于使对象释放资源（如关闭连接、关闭文件），之后才进行垃圾回收，这个方法一般不会显示的调用，在垃圾回收时垃圾回收器会主动调用。


* 序列化的方式


* Serializable 和Parcelable 的区别


* 静态属性和静态方法是否可以被继承？是否可以被重写？以及原因？


不可以

* 静态内部类的设计意图


* 成员内部类、静态内部类、局部内部类和匿名内部类的理解，以及项目中的应用

成员内部类可以无条件地访问外部类的成员，而外部类想访问成员内部类的成员却不是这么随心所欲了。在外部类中如果要访问成员内部类的成员，必须先创建一个成员内部类的对象，再通过指向这个对象的引用来访问。
成员内部类是依附外部类而存在的，也就是说，如果要创建成员内部类的对象，前提是必须存在一个外部类的对象。


局部内部类是定义在一个方法或者一个作用域里面的类，它和成员内部类的区别在于局部内部类的访问仅限于方法内或者该作用域内。
注意，局部内部类就像是方法里面的一个局部变量一样，是不能有public、protected、private以及static修饰符的。

匿名内部类应该是平时我们编写代码时用得最多的，在编写事件监听的代码时使用匿名内部类不但方便，而且使代码更加容易维护。
匿名内部类是唯一一种没有构造器的类。正因为其没有构造器，所以匿名内部类的使用范围非常有限，大部分匿名内部类用于接口回调。匿名内部类在编译的时候由系统自动起名为Outter$1.class。一般来说，匿名内部类用于继承其他类或是实现接口，并不需要增加额外的方法，只是对继承方法的实现或是重写。

静态内部类也是定义在另一个类里面的类，只不过在类的前面多了一个关键字static。静态内部类是不需要依赖于外部类的，这点和类的静态成员属性有点类似，并且它不能使用外部类的非static成员变量或者方法，这点很好理解，因为在没有外部类的对象的情况下，可以创建静态内部类的对象，如果允许访问外部类的非static成员就会产生矛盾，因为外部类的非static成员必须依附于具体的对象。

https://www.cnblogs.com/latter/p/5665015.html


* 谈谈对kotlin的理解


* 闭包和局部内部类的区别


* string 转换成 integer的方式及原理