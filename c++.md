# C++ 基本语法

- **对象 -** 对象具有状态和行为。例如：一只狗的状态 - 颜色、名称、品种，行为 - 摇动、叫唤、吃。对象是类的实例。
- **类 -** 类可以定义为描述对象行为/状态的模板/蓝图。
- **方法 -** 从基本上说，一个方法表示一种行为。一个类可以包含多个方法。可以在方法中写入逻辑、操作数据以及执行所有的动作。
- **即时变量 -** 每个对象都有其独特的即时变量。对象的状态是由这些即时变量的值创建的。

```c++
#include <iostream>
using namespace std;
 
// main() 是程序开始执行的地方
 
int main()
{
   cout << "Hello World"; // 输出 Hello World
   return 0;
}
```

- C++ 语言定义了一些头文件，这些头文件包含了程序中必需的或有用的信息。上面这段程序中，包含了头文件 **<iostream>**。
- 下一行 using namespace std; 告诉编译器使用 std 命名空间。命名空间是 C++ 中一个相对新的概念。
- 下一行 // main() 是程序开始执行的地方** 是一个单行注释。单行注释以 // 开头，在行末结束。
- 下一行 int main() 是主函数，程序从这里开始执行。
- 下一行 cout<< "Hello World";会在屏幕上显示消息 "Hello World"。
- 下一行 return 0;终止 main( )函数，并向调用进程返回值 0。

# C++ 变量作用域

一般来说有三个地方可以定义变量：

- 在函数或一个代码块内部声明的变量，称为**局部变量**。
- 在函数参数的定义中声明的变量，称为**形式参数**。
- 在所有函数外部声明的变量，称为**全局变量**。

作用域是程序的一个区域，变量的作用域可以分为以下几种：

- **局部作用域**：在函数内部声明的变量具有局部作用域，它们只能在函数内部访问。局部变量在函数每次被调用时被创建，在函数执行完后被销毁。
- **全局作用域**：在所有函数和代码块之外声明的变量具有全局作用域，它们可以被程序中的任何函数访问。全局变量在程序开始时被创建，在程序结束时被销毁。
- **块作用域**：在代码块内部声明的变量具有块作用域，它们只能在代码块内部访问。块作用域变量在代码块每次被执行时被创建，在代码块执行完后被销毁。
- **类作用域**：在类内部声明的变量具有类作用域，它们可以被类的所有成员函数访问。类作用域变量的生命周期与类的生命周期相同。

**注意：**如果在内部作用域中声明的变量与外部作用域中的变量同名，则内部作用域中的变量将覆盖外部作用域中的变量。

## 局部变量

在函数或一个代码块内部声明的变量，称为局部变量。它们只能被函数内部或者代码块内部的语句使用。

```c++
#include <iostream>
using namespace std;
 
int main ()
{
  // 局部变量声明
  int a, b;
  int c;
 
  // 实际初始化
  a = 10;
  b = 20;
  c = a + b;
 
  cout << c;
 
  return 0;
}
```

## 全局变量

在所有函数外部定义的变量（通常是在程序的头部），称为全局变量。全局变量的值在程序的整个生命周期内都是有效的。

全局变量可以被任何函数访问。也就是说，全局变量一旦声明，在整个程序中都是可用的

```c++
#include <iostream>
using namespace std;
 
// 全局变量声明
int g;
 
int main ()
{
  // 局部变量声明
  int a, b;
 
  // 实际初始化
  a = 10;
  b = 20;
  g = a + b;
 
  cout << g;
 
  return 0;
}
```

在程序中，局部变量和全局变量的名称可以相同，但是在函数内，局部变量的值会覆盖全局变量的值。

```c++
#include <iostream>
using namespace std;
 
// 全局变量声明
int g = 20;
 
int main ()
{
  // 局部变量声明
  int g = 10;
 
  cout << g;
 
  return 0;
}
```

## 初始化局部变量和全局变量

当局部变量被定义时，系统不会对其初始化，您必须自行对其初始化。定义全局变量时，系统会自动初始化为下列值

| int     | 0    |
| ------- | ---- |
| char    | '\0' |
| float   | 0    |
| double  | 0    |
| pointer | NULL |

块作用域指的是在代码块内部声明的变量：

```c++
#include <iostream>

int main() {
    int a = 10;
    {
        int a = 20;  // 块作用域变量
        std::cout << "块变量: " << a << std::endl;
    }
    std::cout << "外部变量: " << a << std::endl;
    return 0;
}
```

内部的代码块中声明了一个名为 a 的变量，它与外部作用域中的变量 a 同名。内部作用域中的变量 a 将覆盖外部作用域中的变量 a，在内部作用域中访问 a 时输出的是20，而在外部作用域中访问 a 时输出的是 10。

## 类作用域

类作用域指的是在类内部声明的变量：

```c++
#include <iostream>

class MyClass {
public:
    static int class_var;  // 类作用域变量
};

int MyClass::class_var = 30;

int main() {
    std::cout << "类变量: " << MyClass::class_var << std::endl;
    return 0;
}
```

## 定义常量

在 C++ 中，有两种简单的定义常量的方式：

- 使用 #define预处理器。
- 使用const 关键字。

## #define 预处理器

下面是使用 #define 预处理器定义常量的形式

```c++
#define identifier value

#include <iostream>
using namespace std;
 
#define LENGTH 10   
#define WIDTH  5
#define NEWLINE '\n'
 
int main()
{
 
   int area;  
   
   area = LENGTH * WIDTH;
   cout << area;
   cout << NEWLINE;
   return 0;
}
50
```

## const关键字

您可以使用const前缀声明指定类型的常量

```c++
const type variable = value;
#include <iostream>
using namespace std;
 
int main()
{
   const int  LENGTH = 10;
   const int  WIDTH  = 5;
   const char NEWLINE = '\n';
   int area;  
   
   area = LENGTH * WIDTH;
   cout << area;
   cout << NEWLINE;
   return 0;
}
50
```

# C++ 修饰符类型

C++ 允许在 **char、int 和 double** 数据类型前放置修饰符。

修饰符是用于改变变量类型的行为的关键字，它更能满足各种情境的需求。

下面列出了数据类型修饰符：

- signed：表示变量可以存储负数。对于整型变量来说，signed 可以省略，因为整型变量默认为有符号类型。
- unsigned：表示变量不能存储负数。对于整型变量来说，unsigned 可以将变量范围扩大一倍。
- short：表示变量的范围比 int 更小。short int 可以缩写为 short。
- long：表示变量的范围比 int 更大。long int 可以缩写为 long。
- long long：表示变量的范围比 long 更大。C++11 中新增的数据类型修饰符。
- float：表示单精度浮点数。
- double：表示双精度浮点数。
- bool：表示布尔类型，只有 true 和 false 两个值。
- char：表示字符类型。
- wchar_t：表示宽字符类型，可以存储 Unicode 字符。

修饰符 **signed、unsigned、long 和 short** 可应用于整型，**signed** 和 **unsigned** 可应用于字符型，**long** 可应用于双精度型。

这些修饰符也可以组合使用，修饰符 **signed** 和 **unsigned** 也可以作为 **long** 或 **short** 修饰符的前缀。例如：**unsigned long int**。

C++ 允许使用速记符号来声明**无符号短整数**或**无符号长整数**。

# C++ 存储类

存储类定义 C++ 程序中变量/函数的范围（可见性）和生命周期。这些说明符放置在它们所修饰的类型之前。下面列出 C++ 程序中可用的存储类：

- **auto**：这是默认的存储类说明符，通常可以省略不写。auto 指定的变量具有自动存储期，即它们的生命周期仅限于定义它们的块（block）。auto 变量通常在栈上分配。
- **register**：用于建议编译器将变量存储在CPU寄存器中以提高访问速度。在 C++11 及以后的版本中，register 已经是一个废弃的特性，不再具有实际作用。
- **static**：用于定义具有静态存储期的变量或函数，它们的生命周期贯穿整个程序的运行期。在函数内部，static变量的值在函数调用之间保持不变。在文件内部或全局作用域，static变量具有内部链接，只能在定义它们的文件中访问。
- **extern**：用于声明具有外部链接的变量或函数，它们可以在多个文件之间共享。默认情况下，全局变量和函数具有 extern 存储类。在一个文件中使用extern声明另一个文件中定义的全局变量或函数，可以实现跨文件共享。
- **mutable (C++11)**：用于修饰类中的成员变量，允许在const成员函数中修改这些变量的值。通常用于缓存或计数器等需要在const上下文中修改的数据。
- **thread_local (C++11)**：用于定义具有线程局部存储期的变量，每个线程都有自己的独立副本。线程局部变量的生命周期与线程的生命周期相同。

## register 存储类

register 是一种存储类（storage class），用于声明变量，并提示编译器将这些变量存储在寄存器中，以便快速访问。

使用 register 关键字可以提高程序的执行速度，因为它减少了对内存的访问次数。

```c++
register data_type variable_name;

void loop() {
    register int i;
    for (i = 0; i < 1000; ++i) {
        // 循环体
    }
}
```

- `register` 是存储类的关键字，用于提示编译器将变量存储在寄存器中。
- `data_type` 是变量的数据类型，可以是任何合法的 C++ 数据类型。
- `variable_name` 是变量的名称

register 存储类用于提示编译器将变量存储在寄存器中，以便提高访问速度。然而，由于现代编译器的自动优化能力，使用 register 关键字并不是必需的，而且在实践中很少使用。

## static 存储类

**static** 存储类指示编译器在程序的生命周期内保持局部变量的存在，而不需要在每次它进入和离开作用域时进行创建和销毁。因此，使用 static 修饰局部变量可以在函数调用之间保持局部变量的值。

static 修饰符也可以应用于全局变量。当 static 修饰全局变量时，会使变量的作用域限制在声明它的文件内。

```c++
#include <iostream>
 
// 函数声明 
void func(void);
 
static int count = 10; /* 全局变量 */
 
int main()
{
    while(count--)
    {
       func();
    }
    return 0;
}
// 函数定义
void func( void )
{
    static int i = 5; // 局部静态变量
    i++;
    std::cout << "变量 i 为 " << i ;
    std::cout << " , 变量 count 为 " << count << std::endl;
}
```

## extern 存储类

**extern** 存储类用于提供一个全局变量的引用，全局变量对所有的程序文件都是可见的。当您使用 'extern' 时，对于无法初始化的变量，会把变量名指向一个之前定义过的存储位置。

当您有多个文件且定义了一个可以在其他文件中使用的全局变量或函数时，可以在其他文件中使用 *extern* 来得到已定义的变量或函数的引用。可以这么理解，*extern* 是用来在另一个文件中声明一个全局变量或函数。

extern 修饰符通常用于当有两个或多个文件共享相同的全局变量或函数的时候，如下所示：

```c++
第一个文件：main.cpp
#include <iostream>
 
int count ;
extern void write_extern();
 
int main()
{
   count = 5;
   write_extern();
}

第二个文件：support.cpp
#include <iostream>
 
extern int count;
 
void write_extern(void)
{
   std::cout << "Count is " << count << std::endl;
}
```

## mutable 存储类

mutable 是一个关键字，用于修饰类的成员变量，使其能够在 const 成员函数中被修改。通常情况下，const 成员函数不能修改对象的状态，但如果某个成员变量被声明为 mutable，则可以在 const 函数中对其进行修改。

**特点：**

- **允许修改**：`mutable` 成员变量可以在 `const` 成员函数内被改变。
- **设计目的**：通常用于需要在不改变对象外部状态的情况下进行状态管理的场景，比如缓存、延迟计算等。

```c++
#include <iostream>

class Example {
public:
    Example() : value(0), cachedValue(0) {}

    // 常量成员函数
    int getValue() const {
        return value; // 读取常量成员
    }

    // 修改 mutable 成员
    void increment() {
        ++value;
        cachedValue = value * 2; // 修改 mutable 成员
    }

    int getCachedValue() const {
        return cachedValue; // 读取 mutable 成员
    }

private:
    int value;                 // 常规成员，不能在 const 函数中修改
    mutable int cachedValue;   // 可修改成员，可以在 const 函数中修改
};

int main() {
    const Example ex;
    // ex.increment(); // 错误：无法在 const 对象上调用非 const 函数
    // ex.value = 10;  // 错误：无法修改 const 对象的成员

    std::cout << "Value: " << ex.getValue() << std::endl;
    std::cout << "Cached Value: " << ex.getCachedValue() << std::endl; // 输出为 0

    return 0;
}
```

**适用场景：**

- **缓存**：在 `const` 函数中计算并缓存结果，而不影响对象的外部状态。
- **状态跟踪**：如日志计数器，跟踪调用次数等信息，避免对类的逻辑进行侵入式修改。

**注意事项：**

- `mutable` 变量的使用应谨慎，以免导致意外的状态变化，影响代码的可读性和可维护性。
- `mutable` 适用于需要在 `const` 环境中更改状态的特定情况，而不是普遍的设计模式。

## thread_local 存储类

thread_local 是 C++11 引入的一种存储类，用于在多线程环境中管理线程特有的变量。

使用 thread_local 修饰的变量在每个线程中都有独立的实例，因此每个线程对该变量的操作不会影响其他线程。

- **独立性**：每个线程都有自己独立的变量副本，不同线程之间的读写操作互不干扰。
- **生命周期**：`thread_local` 变量在其线程结束时自动销毁。
- **初始化**：`thread_local` 变量可以进行静态初始化或动态初始化，支持在声明时初始化。

thread_local 适合用于需要存储线程状态、缓存或者避免数据竞争的场景，如线程池、请求上下文等。

以下演示了可以被声明为 thread_local 的变量：

```c++
#include <iostream>
#include <thread>
 
thread_local int threadSpecificVar = 0; // 每个线程都有自己的 threadSpecificVar
 
void threadFunction(int id) {
    threadSpecificVar = id; // 设置线程特有的变量
    std::cout << "Thread " << id << ": threadSpecificVar = " << threadSpecificVar << std::endl;
}
 
int main() {
    std::thread t1(threadFunction, 1);
    std::thread t2(threadFunction, 2);
 
    t1.join();
    t2.join();
 
    return 0;
}
```

**注意事项：**

- **性能**：由于每个线程都有独立的副本，`thread_local` 变量的访问速度可能比全局或静态变量稍慢。
- **静态存储**：`thread_local` 变量的存储类型为静态存储持续时间，因此在程序整个运行期间会一直存在。

**switch** 语句必须遵循下面的规则：

- **switch** 语句中的 **expression** 必须是一个整型或枚举类型，或者是一个 class 类型，其中 class 有一个单一的转换函数将其转换为整型或枚举类型。
- 在一个 switch 中可以有任意数量的 case 语句。每个 case 后跟一个要比较的值和一个冒号。
- case 的 **constant-expression** 必须与 switch 中的变量具有相同的数据类型，且必须是一个常量或字面量。
- 当被测试的变量等于 case 中的常量时，case 后跟的语句将被执行，直到遇到 **break** 语句为止。
- 当遇到 **break** 语句时，switch 终止，控制流将跳转到 switch 语句后的下一行。
- 不是每一个 case 都需要包含 **break**。如果 case 语句不包含 **break**，控制流将会 *继续* 后续的 case，直到遇到 break 为止。
- 一个 **switch** 语句可以有一个可选的 **default** case，出现在 switch 的结尾。default case 可用于在上面所有 case 都不为真时执行一个任务。default case 中的 **break** 语句不是必需的。

# C++ 函数

函数是一组一起执行一个任务的语句。每个 C++ 程序都至少有一个函数，即主函数 **main()** ，所有简单的程序都可以定义其他额外的函数。

您可以把代码划分到不同的函数中。如何划分代码到不同的函数中是由您来决定的，但在逻辑上，划分通常是根据每个函数执行一个特定的任务来进行的。

函数**声明**告诉编译器函数的名称、返回类型和参数。函数**定义**提供了函数的实际主体。

在 C++ 中，函数由一个函数头和一个函数主体组成。下面列出一个函数的所有组成部分：

- **返回类型：**一个函数可以返回一个值。**return_type** 是函数返回的值的数据类型。有些函数执行所需的操作而不返回值，在这种情况下，return_type 是关键字 **void**。
- **函数名称：**这是函数的实际名称。函数名和参数列表一起构成了函数签名。
- **参数：**参数就像是占位符。当函数被调用时，您向参数传递一个值，这个值被称为实际参数。参数列表包括函数参数的类型、顺序、数量。参数是可选的，也就是说，函数可能不包含参数。
- **函数主体：**函数主体包含一组定义函数执行任务的语句。

| 调用类型                                                     | 描述                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [传值调用](https://www.runoob.com/cplusplus/cpp-function-call-by-value.html) | 该方法把参数的实际值赋值给函数的形式参数。在这种情况下，修改函数内的形式参数对实际参数没有影响。 |
| [指针调用](https://www.runoob.com/cplusplus/cpp-function-call-by-pointer.html) | 该方法把参数的地址赋值给形式参数。在函数内，该地址用于访问调用中要用到的实际参数。这意味着，修改形式参数会影响实际参数。 |
| [引用调用](https://www.runoob.com/cplusplus/cpp-function-call-by-reference.html) | 该方法把参数的引用赋值给形式参数。在函数内，该引用用于访问调用中要用到的实际参数。这意味着，修改形式参数会影响实际参数。 |

默认情况下，C++ 使用**传值调用**来传递参数。一般来说，这意味着函数内的代码不能改变用于调用函数的参数。之前提到的实例，调用 max() 函数时，使用了相同的方法。

## 参数的默认值

当您定义一个函数，您可以为参数列表中后边的每一个参数指定默认值。当调用函数时，如果实际参数的值留空，则使用这个默认值。

这是通过在函数定义中使用赋值运算符来为参数赋值的。调用函数时，如果未传递参数的值，则会使用默认值，如果指定了值，则会忽略默认值，使用传递的值。

## Lambda 函数与表达式

C++11 提供了对匿名函数的支持,称为 Lambda 函数(也叫 Lambda 表达式)。

Lambda 表达式把函数看作对象。Lambda 表达式可以像对象一样使用，比如可以将它们赋给变量和作为参数传递，还可以像函数一样对其求值。

Lambda 表达式本质上与函数声明非常类似。Lambda 表达式具体形式如下:

```c++
[capture](parameters)->return-type{body}
例如：
[](int x, int y){ return x < y ; }

如果没有返回值可以表示为：
[capture](parameters){body}
例如：
[]{ ++global_x; } 

在一个更为复杂的例子中，返回类型可以被明确的指定如下：
[](int x, int y) -> int { int z = x + y; return z + x; }
```

一个临时的参数 z 被创建用来存储中间结果。如同一般的函数，z 的值不会保留到下一次该不具名函数再次被调用时。

如果 lambda 函数没有传回值（例如 void），其返回类型可被完全忽略。

在Lambda表达式内可以访问当前作用域的变量，这是Lambda表达式的闭包（Closure）行为。 与JavaScript闭包不同，C++变量传递有传值和传引用的区别。可以通过前面的[]来指定:

```
[]      // 沒有定义任何变量。使用未定义变量会引发错误。
[x, &y] // x以传值方式传入（默认），y以引用方式传入。
[&]     // 任何被使用到的外部变量都隐式地以引用方式加以引用。
[=]     // 任何被使用到的外部变量都隐式地以传值方式加以引用。
[&, x]  // x显式地以传值方式加以引用。其余变量以引用方式加以引用。
[=, &z] // z显式地以引用方式加以引用。其余变量以传值方式加以引用。
```

另外有一点需要注意。对于[=]或[&]的形式，lambda 表达式可以直接使用 this 指针。但是，对于[]的形式，如果要使用 this 指针，必须显式传入：

```
[this]() { this->someFunc(); }();
```

# C++ 指针

学习 C++ 的指针既简单又有趣。通过指针，可以简化一些 C++ 编程任务的执行，还有一些任务，如动态内存分配，没有指针是无法执行的。所以，想要成为一名优秀的 C++ 程序员，学习指针是很有必要的。

正如您所知道的，每一个变量都有一个内存位置，每一个内存位置都定义了可使用连字号（&）运算符访问的地址，它表示了在内存中的一个地址。请看下面的实例，它将输出定义的变量地址：

```c++
#include <iostream>
 
using namespace std;
 
int main ()
{
   int  var1;
   char var2[10];
 
   cout << "var1 变量的地址： ";
   cout << &var1 << endl;
 
   cout << "var2 变量的地址： ";
   cout << &var2 << endl;
 
   return 0;
}

var1 变量的地址： 0xbfebd5c0
var2 变量的地址： 0xbfebd5b6
```

## 什么是指针？

**指针**是一个变量，其值为另一个变量的地址，即，内存位置的直接地址。就像其他变量或常量一样，您必须在使用指针存储其他变量地址之前，对其进行声明。指针变量声明的一般形式为

```c++
type *var-name;
在这里，type 是指针的基类型，它必须是一个有效的 C++ 数据类型，var-name 是指针变量的名称。用来声明指针的星号 * 与乘法中使用的星号是相同的。但是，在这个语句中，星号是用来指定一个变量是指针。以下是有效的指针声明
int    *ip;    /* 一个整型的指针 */
double *dp;    /* 一个 double 型的指针 */
float  *fp;    /* 一个浮点型的指针 */
char   *ch;    /* 一个字符型的指针 */

```

所有指针的值的实际数据类型，不管是整型、浮点型、字符型，还是其他的数据类型，都是一样的，都是一个代表内存地址的长的十六进制数。不同数据类型的指针之间唯一的不同是，指针所指向的变量或常量的数据类型不同。

## C++ 中使用指针

使用指针时会频繁进行以下几个操作：定义一个指针变量、把变量地址赋值给指针、访问指针变量中可用地址的值。这些是通过使用一元运算符 ***** 来返回位于操作数所指定地址的变量的值。

```c++
#include <iostream>
 
using namespace std;
 
int main ()
{
   int  var = 20;   // 实际变量的声明
   int  *ip;        // 指针变量的声明
 
   ip = &var;       // 在指针变量中存储 var 的地址
 
   cout << "Value of var variable: ";
   cout << var << endl;
 
   // 输出在指针变量中存储的地址
   cout << "Address stored in ip variable: ";
   cout << ip << endl;
 
   // 访问指针中地址的值
   cout << "Value of *ip variable: ";
   cout << *ip << endl;
 
   return 0;
}

Value of var variable: 20
Address stored in ip variable: 0xbfc601ac
Value of *ip variable: 20
```

| 概念                                                         | 描述                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [C++ Null 指针](https://www.runoob.com/cplusplus/cpp-null-pointers.html) | C++ 支持空指针。NULL 指针是一个定义在标准库中的值为零的常量。 |
| [C++ 指针的算术运算](https://www.runoob.com/cplusplus/cpp-pointer-arithmetic.html) | 可以对指针进行四种算术运算：++、--、+、-                     |
| [C++ 指针 vs 数组](https://www.runoob.com/cplusplus/cpp-pointers-vs-arrays.html) | 指针和数组之间有着密切的关系。                               |
| [C++ 指针数组](https://www.runoob.com/cplusplus/cpp-array-of-pointers.html) | 可以定义用来存储指针的数组。                                 |
| [C++ 指向指针的指针](https://www.runoob.com/cplusplus/cpp-pointer-to-pointer.html) | C++ 允许指向指针的指针。                                     |
| [C++ 传递指针给函数](https://www.runoob.com/cplusplus/cpp-passing-pointers-to-functions.html) | 通过引用或地址传递参数，使传递的参数在调用函数中被改变。     |
| [C++ 从函数返回指针](https://www.runoob.com/cplusplus/cpp-return-pointer-from-functions.html) | C++ 允许函数返回指针到局部变量、静态变量和动态内存分配。     |

# C++ 指针的算术运算

指针是一个用数值表示的地址。因此，您可以对指针执行算术运算。可以对指针进行四种算术运算：++、--、+、-。

假设 **ptr** 是一个指向地址 1000 的整型指针，是一个 32 位的整数，让我们对该指针执行下列的算术运算：

```c++
ptr++
```

执行 ptr++ 后，指针 ptr 会向前移动 4 个字节，指向下一个整型元素的地址。这是由于指针算术运算会根据指针的类型和大小来决定移动的距离。在这种情况下，由于是一个 32 位整数指针，每个整数占据 4 个字节，因此 ptr++ 会将指针 ptr 向前移动 4 个字节，指向下一个整型元素的地址。

如果 **ptr** 指向一个地址为 1000 的字符，执行 ptr++ 指针 ptr 的值会增加，指向下一个字符元素的地址，由于 ptr 是一个字符指针，每个字符占据 1 个字节，因此 ptr++ 会将 ptr 的值增加 1，执行后 ptr 指向地址 1001。

指针算术运算的详细解析：

- 加法运算：可以对指针进行加法运算。当一个指针p加上一个整数n时，结果是指针p向前移动n个元素的大小。例如，如果p是一个int类型的指针，每个int占4个字节，那么p + 1将指向p所指向的下一个int元素。
- 减法运算：可以对指针进行减法运算。当一个指针p减去一个整数n时，结果是指针p向后移动n个元素的大小。例如，如果p是一个int类型的指针，每个int占4个字节，那么p - 1将指向p所指向的前一个int元素。
- 指针与指针之间的减法运算：可以计算两个指针之间的距离。当从一个指针p减去另一个指针q时，结果是两个指针之间的元素个数。例如，如果p和q是两个int类型的指针，每个int占4个字节，那么p - q将得到两个指针之间的元素个数。
- 指针与整数之间的比较运算：可以将指针与整数进行比较运算。可以使用关系运算符（如<、>、<=、>=）对指针和整数进行比较。这种比较通常用于判断指针是否指向某个有效的内存位置。

## 递增一个指针

在C++中，指针是一个变量，它存储一个内存地址。递增一个指针意味着将指针指向下一个内存位置，这通常是指向下一个数组元素。递增一个指针会根据指针所指向的数据类型自动调整指针的值。

例如，如果指针指向一个 int 类型的数组元素，那么递增指针将使其指向下一个 int 元素。下面是一个简单的示例，演示了如何递增一个指针：

```c++
#include <iostream>
 
int main() {
    // 定义一个数组
    int arr[] = {10, 20, 30, 40, 50};
    
    // 定义一个指向数组第一个元素的指针
    int* ptr = arr;
    
    // 输出指针指向的元素
    std::cout << "指针当前指向的元素: " << *ptr << std::endl;
    
    // 递增指针
    ptr++;
    
    // 输出指针指向的元素
    std::cout << "递增指针后指向的元素: " << *ptr << std::endl;
    
    return 0;
}
指针当前指向的元素: 10
递增指针后指向的元素: 20

```

在这个示例中，指针 `ptr` 最初指向数组 `arr` 的第一个元素。通过执行 `ptr++`，指针 `ptr` 被递增以指向数组的下一个元素（即第二个元素）。

递增指针时，指针的值将增加一个偏移量，该偏移量等于指针所指向数据类型的大小。例如，如果指针是 `int*` 类型，每次递增指针将增加4个字节（假设 `int` 类型占4个字节）。

需要注意的是，当使用指针操作时，要确保指针指向有效的内存区域，否则可能会导致未定义行为或程序崩溃。在操作数组时，尤其要小心避免指针超出数组的范围。

## 递减一个指针

在C++中，指针不仅可以递增，也可以递减。递减一个指针意味着将指针指向前一个内存位置。与递增指针类似，递减指针也会根据指针所指向的数据类型自动调整指针的值。

下面是一个简单的示例，演示了如何递减一个指针：

```c++
#include <iostream>
 
int main() {
    // 定义一个数组
    int arr[] = {10, 20, 30, 40, 50};
    
    // 定义一个指向数组第二个元素的指针
    int* ptr = &arr[1];
    
    // 输出指针当前指向的元素
    std::cout << "指针当前指向的元素: " << *ptr << std::endl;
    
    // 递减指针
    ptr--;
    
    // 输出指针递减后指向的元素
    std::cout << "递减指针后指向的元素: " << *ptr << std::endl;
    
    return 0;
}
指针当前指向的元素: 20
递减指针后指向的元素: 10

```

在这个示例中，指针 `ptr` 最初指向数组 `arr` 的第二个元素。通过执行 `ptr--`，指针 `ptr` 被递减以指向数组的第一个元素。

递减指针时，指针的值将减少一个偏移量，该偏移量等于指针所指向数据类型的大小。例如，如果指针是 `int*` 类型，每次递减指针将减少4个字节（假设 `int` 类型占4个字节）。

## 指针的比较

在C++中，指针的比较操作可以用于确定两个指针是否指向相同的位置、一个指针是否指向的位置在另一个指针之前或之后等。指针的比较主要包括以下几种：

- **相等性比较** (`==` 和 `!=`)
- **关系比较** (`<`, `<=`, `>`, `>=`)

### 相等性比较

相等性比较用于检查两个指针是否指向相同的位置。

```c++
#include <iostream>

int main() {
    int a = 10;
    int b = 20;
    int* ptr1 = &a;
    int* ptr2 = &a;
    int* ptr3 = &b;

    // 比较指针是否相等
    if (ptr1 == ptr2) {
        std::cout << "ptr1 和 ptr2 指向相同的位置" << std::endl;
    } else {
        std::cout << "ptr1 和 ptr2 指向不同的位置" << std::endl;
    }

    if (ptr1 != ptr3) {
        std::cout << "ptr1 和 ptr3 指向不同的位置" << std::endl;
    } else {
        std::cout << "ptr1 和 ptr3 指向相同的位置" << std::endl;
    }

    return 0;
}
ptr1 和 ptr2 指向相同的位置
ptr1 和 ptr3 指向不同的位置
```

### 关系比较

关系比较用于确定一个指针是否指向的位置在另一个指针之前或之后。这通常在指针指向同一个数组的元素时有意义。

```c++
#include <iostream>

int main() {
    int arr[] = {10, 20, 30, 40, 50};
    int* ptr1 = &arr[1]; // 指向数组的第二个元素
    int* ptr2 = &arr[3]; // 指向数组的第四个元素

    // 比较指针的相对位置
    if (ptr1 < ptr2) {
        std::cout << "ptr1 指向的元素在 ptr2 指向的元素之前" << std::endl;
    } else {
        std::cout << "ptr1 指向的元素不在 ptr2 指向的元素之前" << std::endl;
    }

    if (ptr2 > ptr1) {
        std::cout << "ptr2 指向的元素在 ptr1 指向的元素之后" << std::endl;
    } else {
        std::cout << "ptr2 指向的元素不在 ptr1 指向的元素之后" << std::endl;
    }

    return 0;
}
ptr1 指向的元素在 ptr2 指向的元素之前
ptr2 指向的元素在 ptr1 指向的元素之后
```

### 注意事项

- **同一数组范围内的比较**： 关系比较（如 `<`, `>`, `<=`, `>=`）在同一数组的元素之间进行是有意义的。如果指针不属于同一个数组，关系比较的结果是未定义的。
- **指针为空**： 在比较指针之前，确保指针不是空指针（`nullptr`），否则可能会导致未定义行为。

# C++ 指针 vs 数组

指针和数组是密切相关的。事实上，指针和数组在很多情况下是可以互换的。例如，一个指向数组开头的指针，可以通过使用指针的算术运算或数组索引来访问数组。请看下面的程序：

```c++
#include <iostream>
 
using namespace std;
const int MAX = 3;
 
int main ()
{
   int  var[MAX] = {10, 100, 200};
   int  *ptr;
 
   // 指针中的数组地址
   ptr = var;
   for (int i = 0; i < MAX; i++)
   {
      cout << "var[" << i << "]的内存地址为 ";
      cout << ptr << endl;
 
      cout << "var[" << i << "] 的值为 ";
      cout << *ptr << endl;
 
      // 移动到下一个位置
      ptr++;
   }
   return 0;
}
var[0]的内存地址为 0x7fff59707adc
var[0] 的值为 10
var[1]的内存地址为 0x7fff59707ae0
var[1] 的值为 100
var[2]的内存地址为 0x7fff59707ae4
var[2] 的值为 200

    
然而，指针和数组并不是完全互换的。

#include <iostream>
using namespace std;
const int MAX = 3;
 
int main ()
{
   int  var[MAX] = {10, 100, 200};
 
   for (int i = 0; i < MAX; i++)
   {
      *var = i;    // 这是正确的语法
      var++;       // 这是不正确的
   }
   return 0;
}
```

把指针运算符 * 应用到 var 上是完全可以的，但修改 var 的值是非法的。这是因为 var 是一个指向数组开头的常量，不能作为左值。

由于一个数组名对应一个指针常量，只要不改变数组的值，仍然可以用指针形式的表达式。例如，下面是一个有效的语句，把 var[2] 赋值为 500：

```c++
*(var + 2) = 500;
```

# C++ 指针数组
