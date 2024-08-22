# 面向对象

### java的包

src.com.com_name.project_name.module_name.class_name.java

这里简要解释一下每个修饰符的可访问范围：

1. **public（公共）**：成员可以被任何其他类访问，不论这些类是否在同一包内或是子类。
2. **protected（受保护）**：成员可以被同一包内的类以及任何子类访问，无论子类是否在同一包内。
3. **默认（无修饰符，也称包访问权限）**：成员只能被同一包内的类访问。
4. **private（私有）**：成员只能在其所在的类内被访问。

封装

继承

多态

1. 向上转型

   ~~~
   Animal myAnimal = new Dog();
   ~~~

   

2. 向下转型

   ~~~
   if (myAnimal instanceof Dog) {
       Dog myDog = (Dog) myAnimal;
       myDog.bark(); // 输出: Dog barks
   }
   //错误示例
   Animal anotherAnimal = new Animal();
   Dog myDog = (Dog) anotherAnimal; // 这会导致运行时异常，因为anotherAnimal不是Dog实例
   
   ~~~

   

3. 编译的属性就是运行时的属性

   ~~~
   class AAAA {
       // AAAA类的定义
   }
   
   class BBBB extends AAAA {
       // BBBB类继承自AAAA类
   }
   
   public class Main {
       public static void main(String[] args) {
           AAAA bbbb = new BBBB();
           // instanceof 比较操作符，用于判断某个对象的运行类型是否为XX类型或XX类型的子类型
           System.out.println(bbbb instanceof BBBB); // true
           System.out.println(bbbb instanceof AAAA); // true
           System.out.println(bbbb instanceof Object); // true
           
           Object obj = new Object();
           System.out.println(obj instanceof AAAA); // false
       }
   }
   
   ~~~

   ### 输出结果：

   1. `System.out.println(bbbb instanceof BBBB); // true`
      - `bbbb` 的运行时类型是 `BBBB`，所以它是 `BBBB` 的实例，结果为 `true`。
   2. `System.out.println(bbbb instanceof AAAA); // true`
      - `bbbb` 是 `BBBB` 类的对象，而 `BBBB` 类继承自 `AAAA` 类，所以 `bbbb` 也是 `AAAA` 的实例，结果为 `true`。
   3. `System.out.println(bbbb instanceof Object); // true`
      - 所有的 Java 对象都是 `Object` 类的实例，`bbbb` 也是 `Object` 的实例，结果为 `true`。
   4. `System.out.println(obj instanceof AAAA); // false`
      - `obj` 的类型是 `Object`，它不是 `AAAA` 类或其子类的实例，结果为 `false`。

## 调用方法

### 向上转型

~~~
Animal tom=new Cat();
~~~

父类引用指向子类对象

编译类型看左边，运行类型看右边

所以父类型不能调用子类对象特有的方法，编译时认为它是父类型，但继承的子类父类都有的方法实际会调用子类的方法

### 向下转型

如向上转型中的例子所示，tom无法调用Cat独有的方法，因为编译时认为tom是Animal而不是Dog，此时考虑向下强制转型为Dog

~~~
Dog myDog = (Dog) myAnimal; // 向下转型
~~~

## 调用属性

属性重写时，看编译类型而不是运行类型

**instanceof方法看运行类型**

## 动态绑定机制

调用的方法和对象的运行类型绑定

调用的属性不绑定，哪里的方法调用，就调用对应方法所在的对象。属性未在该对象中被定义怎么办

多态数组：父（编译类型）类数组，元素是子类对象，调用子类独有方法时向下转型

多态参数：形参是父类，实参允许是子类，共有方法会覆盖，直接调用，独有方法需要向下转型

## 类变量

