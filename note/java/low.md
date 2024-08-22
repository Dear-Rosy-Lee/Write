# JAVA初级

## 基本语法

Java一切都是面向对象，主函数也是一个对象的方法

打印使用System.out.print()

读取输入使用

~~~
public static Scanner input=new Scanner(System.in);
int x=input.nextInt();
~~~

java中的转义字符使用“”而不是''

java的编译和运行示例

~~~powershell
javac -d build src\com\example\*.java 
java -cp build src.com.example.Main
~~~

定义数组

~~~
int[] a={1,2,3};
int[] a=new int[5];
~~~

数组和对象赋值都是引用（地址）拷贝

java创建对象时，

1. 加载类信息
2. 堆中分配空间（默认值初始化），把地址赋值给p
3. p得到对象地址
4. 指定值初始化

java中函数有重载，但没有默认参数的说法

package关键词用于声明包的名称

