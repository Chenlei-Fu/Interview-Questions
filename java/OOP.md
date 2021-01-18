# Object Oriented Fundamentals
Object-oriented programming (OOP) is a computer programming model that organizes software design around data, or objects, rather than functions and logic. 


## Interview Questions
### Characteristics of an OOP language
1. Polymorphism: Polymorphism refers to the capability of having methods with the same names and parameter types exhibit different behavior depending on the receiver. In other words, you can send the same message to two different objects and they can respond in different ways.
   
多态性是指允许不同子类型的对象对同一消息作出不同的响应。

1. Inheritance: Inheritance refers to the capability of defining a new class of objects that inherits from a parent class. Inheritance gives some continuity to changing software systems, and it's also an important means of encapsualting variable elements in programs. 

继承是从已有类得到继承信息创建新类的过程。继承让变化中的软件系统有了一定的延续性，同时继承也是封装程序中可变因素的重要手段。


3. Encapsulation: Encapsulation refers to mechanisms that allow each object to have its own data and methods. Generally, we believe that encapsulation is to bind data and the methods of manipulating data. The access to data can only be trhough defined interfaces. The essence of object-oriented is to describe the real world as a series of completely autonomous and closed objects. 

封装是指允许每个对象拥有自己的数据和方法的机制。通常认为封装是把数据和操作数据的方法绑定起来，对数据的访问只能通过已定义的接口。面向对象的本质就是将现实世界描绘成一系列完全自治、封闭的对象。

4. Abstraction: Abstraction is the process of constructing a class by summarizing the common features of a class of objects including both data abstraction and behavior abstraction. Abstraction is concerned only with what properties and behaviors an object has and not with what the details of those behaviors are.

抽象是将一类对象的共同特征总结出来构造类的过程，包括数据抽象和行为抽象两方面。抽象只关注对象有哪些属性和行为，并不关注这些行为的细节是什么。

### What is Polymorphism
Polymorphism is the ability of an object to take on many forms. The most common use of polymorphism in OOP occurs when a parent class reference is used to refer to a child class object.

In Java polymorphism is mainly divided into two types:

1. Compile time Polymorphism: It is also known as static polymorphism. This type of polymorphism is achieved by function overloading or operator overloading. But Java doesn’t support the Operator Overloading.
* Method Overloading: When there are multiple functions with same name but different parameters then these functions are said to be overloaded. Functions can be overloaded by change in number of arguments or/and change in type of arguments.

Example: By using different types of arguments / different numbers of arguments
```java
class MultiplyFun { 
    // Method with 2 parameter 
    static int Multiply(int a, int b) { 
        return a * b; 
    } 
  
    // Method with the same name but 2 double parameter 
    static double Multiply(double a, double b) { 
        return a * b; 
    } 
  
    // Method with the same name but 3 parameter 
    static int Multiply(int a, int b, int c) { 
        return a * b * c; 
    } 
} 
  
class Main { 
    public static void main(String[] args) { 
        System.out.println(MultiplyFun.Multiply(2, 4)); 
        System.out.println(MultiplyFun.Multiply(5.5, 6.3)); 
        System.out.println(MultiplyFun.Multiply(2, 7, 3)); 
    } 
} 

```
Output:
```
8
34.65
42
```


2. Runtime Polymorphism
It is also known as Dynamic Method Dispatch. It is a process in which a function call to the overridden method is resolved at Runtime. 
* Override: In any OOPs, overriding is a feature that allows a subclass or child class to provide a specific implementation of a method that is already provided by one of its super-classes or parent classes. 

Example:
```java
class Parent { 
    void Print() { 
        System.out.println("parent class"); 
    } 
} 
  
class subclass1 extends Parent { 
    void Print() { 
        System.out.println("subclass1"); 
    } 
} 
  
class subclass2 extends Parent { 
    void Print() { 
        System.out.println("subclass2"); 
    } 
} 
  
class TestPolymorphism3 { 
    public static void main(String[] args) { 
        Parent a; 
        a = new subclass1(); 
        a.Print(); 
        a = new subclass2(); 
        a.Print(); 
    } 
} 
```

Output:
```
subclass1
subclass2
```



### Overload v.s Override
1. Overriding implements Runtime Polymorphism whereas Overloading implements Compile time polymorphism.
2. The method Overriding occurs between superclass and subclass. Overloading occurs between the methods in the same class.
3. Overriding methods have the same signature i.e. same name and method arguments. Overloaded method names are the same but the parameters are different.
4. With Overloading, the method to call is determined at the compile-time. With overriding, the method call is determined at the runtime based on the object type.
5. If overriding breaks, it can cause serious issues in our program because the effect will be visible at runtime. Whereas if overloading breaks, the compile-time error will come and it’s easy to fix.

方法的重载和重写都是实现多态的方式，区别在于 重载是编译时的多态性，而 重写是运行时的多态性。

重载发生在一个类中，同名的方法如果有不同的参数列表（参数类型不同、参数个数不同或者二者都不同）则视为重载。

重写发生在子类与父类之间，重写要求子类被重写方法与父类被重写方法有相同的返回类型（或子类型），不能比父类被重写方法声明更多的异常（里氏代换原则）。


### Abstract class v.s Interface
#### Interface
a. An interface is a contract: The person writing the interface says, "hey, I accept things looking that way", and the person using the interface says "OK, the class I write looks that way".

b. An interface is an empty shell. There are only the signatures of the methods, which implies that the methods do not have a body. The interface can't do anything. It's just a pattern.

#### Abstract classes
a. Abstract classes, unlike interfaces, are classes. They are more expensive to use, because there is a look-up to do when you inherit from them.

b. Abstract classes look a lot like interfaces, but they have something more: You can define a behavior for them. It's more about a person saying, "these classes should look like that, and they have that in common, so fill in the blanks!".



抽象类和接口都不能够实例化，但可以定义抽象类和接口类型的引用。

一个类如果继承了某个抽象类或者实现了某个接口都需要对其中的抽象方法全部进行实现，否则该类仍然需要被声明为抽象类。

接口比抽象类更加抽象，因为抽象类中可以定义构造器，可以有抽象方法和具体方法，而接口中不能定义构造器而且其中的方法全部都是抽象方法。

抽象类中的成员可以是 private、默认、 protected 、public的，而接口中的成员全都是public的

抽象类中可以定义成员变量，而接口中定义的成员变量实际上都是常量

有抽象方法的类必须被声明为抽象类，而抽象类未必要有抽象方法



### Classes v.s Objects
A class is a blueprint which you use to create objects. An object is a class instance or an array.

### Inheritance v.s Composition
Inheritance is an "is-a" relationship. Composition is a "has-a".
You do composition by having an instance of another class C as a field of your class, instead of extending C. 
Example: Car has a engine and Car is a automobile
```java
class Engine {} // The Engine class.

class Automobile {} // Automobile class which is parent to Car class.

class Car extends Automobile { // Car is an Automobile, so Car class extends Automobile class.
  private Engine engine; // Car has an Engine so, Car class has an instance of Engine class as its member.
}
```





