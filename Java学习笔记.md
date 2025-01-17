# 基础语法

## 一、基本语法

1.大小写敏感

2.类名首字母大写，驼峰式命名

3.方法名，首字母小写，后续单词首字母大写

4.源文件名，与类名必须相同

5.主方法入口

```
public static void main(String[] args)
```



##  二、Java标识符

- 所有的标识符都应该以字母（A-Z 或者 a-z）,美元符（$）、或者下划线（_）开始
- 首字符之后可以是字母（A-Z 或者 a-z）,美元符（$）、下划线（_）或数字的任何字符组合
- 关键字不能用作标识符
- 标识符是大小写敏感的
- 合法标识符举例：age、$salary、_value、__1_value
- 非法标识符举例：123abc、-salary



## 三、Java修饰符

1、访问控制修饰符：default，public，protected，private

2、非访问控制修饰符：final，abstract，static，synchronized



## 四、Java变量

局部变量、类变量（静态变量），成员变量（非静态变量）



## 五、Java数组

数组是储存在堆上的对象，可以保存对个同类型变量



## 六、Java枚举

枚举限制变量只能是预先设定好的值。

```
enum FxxxFxxxFxx{ SMALL, MEDIUM, LARGE }
```

枚举可以单独声明或者声明在类里面。方法、变量、构造函数也可以在枚举中定义。



## 七、Java关键字

|       访问控制       |   private    |             私有的             |
| :------------------: | :----------: | :----------------------------: |
|                      |  protected   |            受保护的            |
|                      |    public    |             公共的             |
|                      |   default    |              默认              |
| 类、方法和变量修饰符 |   abstract   |            声明抽象            |
|                      |    class     |               类               |
|                      |   extends    |           扩充、继承           |
|                      |    final     |       最终值、不可改变的       |
|                      |  implements  |          实现（接口）          |
|                      |  interface   |              接口              |
|                      |    native    | 本地、原生方法（非 Java 实现） |
|                      |     new      |              创建              |
|                      |    static    |              静态              |
|                      |   strictfp   |       严格浮点、精准浮点       |
|                      | synchronized |           线程、同步           |
|                      |  transient   |              短暂              |
|                      |   volatile   |              易失              |
|     程序控制语句     |    break     |            跳出循环            |
|                      |     case     |   定义一个值以供 switch 选择   |
|                      |   continue   |              继续              |
|                      |      do      |              运行              |
|                      |     else     |              否则              |
|                      |     for      |              循环              |
|                      |      if      |              如果              |
|                      |  instanceof  |              实例              |
|                      |    return    |              返回              |
|                      |    switch    |         根据值选择执行         |
|                      |    while     |              循环              |
|       错误处理       |    assert    |       断言表达式是否为真       |
|                      |    catch     |            捕捉异常            |
|                      |   finally    |        有没有异常都执行        |
|                      |    throw     |        抛出一个异常对象        |
|                      |    throws    |     声明一个异常可能被抛出     |
|                      |     try      |            捕获异常            |
|        包相关        |    import    |              引入              |
|                      |   package    |               包               |
|       基本类型       |   boolean    |             布尔型             |
|                      |     byte     |             字节型             |
|                      |     char     |             字符型             |
|                      |    double    |           双精度浮点           |
|                      |    float     |           单精度浮点           |
|                      |     int      |              整型              |
|                      |     long     |             长整型             |
|                      |    short     |             短整型             |
|       变量引用       |    super     |           父类、超类           |
|                      |     this     |              本类              |
|                      |     void     |            无返回值            |
|      保留关键字      |     goto     |      是关键字，但不能使用      |
|                      |    const     |      是关键字，但不能使用      |

## 八、继承

在java中一个类可以由其他类派生，如果要创建一个类，且已经存在一个类具有所需要的属性或方法，那么可以将新创建的类继承该类。

利用继承的方法，可以重用已存在类的方法和属性，不用重写相同代码。被继承的类称为超类，派生类称为子类。



## 九、接口

在java中，接口可理解为对象间相互通信的协议。接口在继承中扮演着很重要的角色。接口只定义派生要用到的方法，但是方法的具体实现完全取决于派生类



# 对象和类

1、**类（Class）**：

- 定义对象的蓝图，包括属性和方法。
- 示例：`public class Car { ... }`

**2、对象（Object）**：

- 类的实例，具有状态和行为。
- 示例：`Car myCar = new Car();`

**3、继承（Inheritance）**：

- 一个类可以继承另一个类的属性和方法。
- 示例：`public class Dog extends Animal { ... }`

**4、封装（Encapsulation）**：

- 将对象的状态（字段）私有化，通过公共方法访问。

- 示例：

  ```
  private String name; 
  public String getName() { return name; }
  ```

**5、多态（Polymorphism）**：

- 对象可以表现为多种形态，主要通过方法重载和方法重写实现。
- 示例：
  - 方法重载：`public int add(int a, int b) { ... }` 和 `public double add(double a, double b) { ... }`
  - 方法重写：`@Override public void makeSound() { System.out.println("Meow"); }`

**6、抽象（Abstraction）**：

- 使用抽象类和接口来定义必须实现的方法，不提供具体实现。
- 示例：
  - 抽象类：`public abstract class Shape { abstract void draw(); }`
  - 接口：`public interface Animal { void eat(); }`

**7、接口（Interface）**：

- 定义类必须实现的方法，支持多重继承。
- 示例：`public interface Drivable { void drive(); }`

**8、方法（Method）**：

- 定义类的行为，包含在类中的函数。
- 示例：`public void displayInfo() { System.out.println("Info"); }`

**9、方法重载（Method Overloading）**：

- 同一个类中可以有多个同名的方法，但参数不同。

  

- **对象**：对象是类的一个实例（**对象不是找个女朋友**），有状态和行为。例如，一条狗是一个对象，它的状态有：颜色、名字、品种；行为有：摇尾巴、叫、吃等。
- **类**：类是一个模板，它描述一类对象的行为和状态。



## 源文件声明规则

- 一个源文件中只能有一个 public 类
- 一个源文件可以有多个非 public 类
- 源文件的名称应该和 public 类的类名保持一致。例如：源文件中 public 类的类名是 Employee，那么源文件应该命名为Employee.java。
- 如果一个类定义在某个包中，那么 package 语句应该在源文件的首行。
- 如果源文件包含 import 语句，那么应该放在 package 语句和类定义之间。如果没有 package 语句，那么 import 语句应该在源文件中最前面。
- import 语句和 package 语句对源文件中定义的所有类都有效。在同一源文件中，不能给不同的类不同的包声明。