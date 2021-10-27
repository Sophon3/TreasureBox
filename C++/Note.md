# 黑马程序员

## C++初识

### 1.0

>```C++
>	std::cout<<输出
>	std::endl<<换行
>    (int)变量//强制转换类型
>    
>```
>
>
>
>

### 1.4常量

C++中定义常量的方法：

>1. #define 常量 数值 //宏定义，宏常量
>
>2. const int/char... 常量 = 数值  //const修饰的变量也是常量
>
>   ```c++
>   #include<iostream>
>   //宏常量，不可修改
>   #define Day 7
>   int main()
>   {
>   	//Day = 7; error
>   	std::cout << "A week have " << Day<<" day"<<std::endl;
>   
>   	const int month = 12;
>   	std::cout << "A year have " << month << " month" << std::endl;
>   	//month = 24; error
>   
>   	system("pause");
>   	return 0;
>   }
>   ```
>
>   



### 1.5关键字                          

关键字系统已经定义了，定义变量时不能使用。

| asm        | do           | if               | return      | typedef  |
| ---------- | ------------ | ---------------- | ----------- | -------- |
| auto       | double       | inline           | short       | typeid   |
| bool       | dynamic_cast | int              | signed      | typename |
| break      | else         | long             | sizeof      | union    |
| case       | enum         | mutable          | static      | unsigned |
| catch      | explicit     | namespace        | static_cast | using    |
| char       | export       | new              | struct      | virtual  |
| class      | extern       | operator         | switch      | void     |
| const      | false        | private          | template    | volatile |
| const_cast | float        | protected        | this        | wchar_t  |
| continue   | for          | public           | throw       | while    |
| default    | friend       | register         | true        |          |
| delete     | goto         | reinterpret_cast | try         |          |





### 1.6 标识符命名规制

>C++标识符（变量and常量）命名规则
>
>+ 标识符不能使用关键字
>+ 标识符只能有字母、数字和下划线组成
>+ 第一个字符必须由字母或下划线组成
>+ 标识符中区分大小写
>
>



## 数据类型

>语法：数据类型 + 变量名 + 变量初值
>
>数据类型的意义：给变量分配合理的内存空间



### 2.1整型

**作用**：表示整数类型的变量

| **数据类型**        | **占用空间**                                    | 取值范围                                    |
| ------------------- | ----------------------------------------------- | ------------------------------------------- |
| short(短整型)       | 2字节                                           | (-2^15 ~ 2^15-1)//-32768-32767              |
| int(整型)           | 4字节                                           | (-2^31 ~ 2^31-1)  //-2147483648～2147483647 |
| long(长整形)        | Windows为4字节，Linux为4字节(32位)，8字节(64位) | (-2^31 ~ 2^31-1)//-2147483648～2147483647   |
| long long(长长整形) | 8字节                                           | (-2^63 ~ 2^63-1)最大9223372036854775807     |



### 2.2 sizeof关键字



>**作用**：统计数据类型所占内存大小 
>
>**语法**：sizeof(数据类型/变量)
>
>```C++
>#include<iostream>
>
>int main()
>{
>	short num1 = 20;
>	std::cout << "var num1 occupied memory space " << sizeof(num1) << std::endl;
>	// num1/short occupied memory space 2 byte
>	long long num2 = 10000000000000000;
>	std::cout << "var num1 occupied memory space " << sizeof(num2) << std::endl;
>	// num2/short occupied memory space 8 byte
>
>	system("pause");
>	return 0;
>}
>```
>
>



### 2.3实型（浮点型）

>**作用**：表示小数
>
>两种类型：
>
>	1. 单精度float
> 	2. 双精度double
>
>| **数据类型** | **占用空间** | **有效数字范围**       |
>| ------------ | ------------ | ---------------------- |
>| float        | 4字节        | ***7位有效数字***      |
>| double       | 8字节        | ***15～16位有效数字*** |
>
> ```C++
> #include<iostream>
> 
> int main()
> {
> 	//默认打印6位有效数字
> 	float f1 = 3.14f;//如果不加f默认为double类型
> 	std::cout << f1 << std::endl;
> 	double f2 = 3.1415926;
> 	std::cout << f2 << std::endl;
> 	std::cout << "occupied memory space " << sizeof(f1) << " in f1 "<<sizeof(f2)<<" in f2 " << std::endl;
> 
> 	//科学计数法
> 	float f3 = 3e2;//3*10^2
> 	std::cout << f3 << std::endl;
> 
> 	float f4 = 3e-2;//3*0.1^2
> 	std::cout << f4 << std::endl;
> 
> 
> 	system("pause");
> 	return 0;
> }
> ```
>
>

### 2.4字符型

>**作用：**显示单个字符
>
>**语法：**char ch = 'a';
>
>+ 单引号
>+ 单引号内只能有一个字符
>
>字符型变量只占一个字节
>
>```C++
>#include<iostream>
>
>int main()
>{
>	char ch = 'a';
>	std::cout<<"ch value is "<< ch << ",ch occupied memory space " << sizeof(ch) << " byte" << std::endl;
>
>	//强制转换类型
>	std::cout <<"ch ASCII is " << (int)ch << std::endl;
>	system("pause");
>	return 0;
>}
>```
>
>

ASCII码表格：

| **ASCII**值 | **控制字符** | **ASCII**值 | **字符** | **ASCII**值 | **字符** | **ASCII**值 | **字符** |
| ----------- | ------------ | ----------- | -------- | ----------- | -------- | ----------- | -------- |
| 0           | NUT          | 32          | (space)  | 64          | @        | 96          | 、       |
| 1           | SOH          | 33          | !        | 65          | A        | 97          | a        |
| 2           | STX          | 34          | "        | 66          | B        | 98          | b        |
| 3           | ETX          | 35          | #        | 67          | C        | 99          | c        |
| 4           | EOT          | 36          | $        | 68          | D        | 100         | d        |
| 5           | ENQ          | 37          | %        | 69          | E        | 101         | e        |
| 6           | ACK          | 38          | &        | 70          | F        | 102         | f        |
| 7           | BEL          | 39          | ,        | 71          | G        | 103         | g        |
| 8           | BS           | 40          | (        | 72          | H        | 104         | h        |
| 9           | HT           | 41          | )        | 73          | I        | 105         | i        |
| 10          | LF           | 42          | *        | 74          | J        | 106         | j        |
| 11          | VT           | 43          | +        | 75          | K        | 107         | k        |
| 12          | FF           | 44          | ,        | 76          | L        | 108         | l        |
| 13          | CR           | 45          | -        | 77          | M        | 109         | m        |
| 14          | SO           | 46          | .        | 78          | N        | 110         | n        |
| 15          | SI           | 47          | /        | 79          | O        | 111         | o        |
| 16          | DLE          | 48          | 0        | 80          | P        | 112         | p        |
| 17          | DCI          | 49          | 1        | 81          | Q        | 113         | q        |
| 18          | DC2          | 50          | 2        | 82          | R        | 114         | r        |
| 19          | DC3          | 51          | 3        | 83          | S        | 115         | s        |
| 20          | DC4          | 52          | 4        | 84          | T        | 116         | t        |
| 21          | NAK          | 53          | 5        | 85          | U        | 117         | u        |
| 22          | SYN          | 54          | 6        | 86          | V        | 118         | v        |
| 23          | TB           | 55          | 7        | 87          | W        | 119         | w        |
| 24          | CAN          | 56          | 8        | 88          | X        | 120         | x        |
| 25          | EM           | 57          | 9        | 89          | Y        | 121         | y        |
| 26          | SUB          | 58          | :        | 90          | Z        | 122         | z        |
| 27          | ESC          | 59          | ;        | 91          | [        | 123         | {        |
| 28          | FS           | 60          | <        | 92          | /        | 124         | \|       |
| 29          | GS           | 61          | =        | 93          | ]        | 125         | }        |
| 30          | RS           | 62          | >        | 94          | ^        | 126         | `        |
| 31          | US           | 63          | ?        | 95          | _        | 127         | DEL      |



### 2.5转义字符

>**作用**：用于表示不能显示的ASCII字符
>
>```c++
>#include<iostream>
>int main()
>{
>	//水平指标符 /t
>	std::cout << "a\thello\n";
>	std::cout << "aa\thello\n";
>	std::cout << "aaa\thello\n";
>	std::cout << "aaaa\thello\n";
>	std::cout << "aaaaa\thello\n";
>	std::cout << "aaaaaaa\thello\n";
>	std::cout << "aaaaaaaa\thello\n";//一个水平制表符占8个空格位置
>	system("pause");
>	return 0;
>}
>```
>
>

现阶段我们常用的转义字符有：` \n  \\  \t`

| **转义字符** | **含义**                                | **ASCII**码值（十进制） |
| ------------ | --------------------------------------- | ----------------------- |
| \a           | 警报                                    | 007                     |
| \b           | 退格(BS) ，将当前位置移到前一列         | 008                     |
| \f           | 换页(FF)，将当前位置移到下页开头        | 012                     |
| **\n**       | **换行(LF) ，将当前位置移到下一行开头** | **010**                 |
| \r           | 回车(CR) ，将当前位置移到本行开头       | 013                     |
| **\t**       | **水平制表(HT)  （跳到下一个TAB位置）** | **009**                 |
| \v           | 垂直制表(VT)                            | 011                     |
| **\\\\**     | **代表一个反斜线字符"\"**               | **092**                 |
| \'           | 代表一个单引号（撇号）字符              | 039                     |
| \"           | 代表一个双引号字符                      | 034                     |
| \?           | 代表一个问号                            | 063                     |
| \0           | 数字0                                   | 000                     |
| \ddd         | 8进制转义字符，d范围0~7                 | 3位8进制                |
| \xhh         | 16进制转义字符，h范围0~9，a~f，A~F      | 3位16进制               |

### 2.6字符串型

>**作用**：表示一串字符
>
>两种类型:
>
>1. C语言风格：` char str[] = "value"` 
>
>   ```c++
>   #include<iostream>
>   
>   int main()
>   {
>   	char str1[] = "hello world";
>   	std::cout << str1 << std::endl;
>   	system("pause");
>   	return 0;
>   }
>   ```
>
>   >1. 双引号
>
>2. C++风格：string str = "value"
>
>   + 与C语言内字符书写一样，string类型
>
>   ```c++
>   #include<iostream>
>   #include<string>
>   
>   int main()
>   {
>   	std::string str1 = "helloworld";
>   	std::cout << str1 << std::endl;
>   	system("pause");
>   	return 0;
>   }
>   ```
>
>   >1. 添加头文件`#include<string>`
>   >2. 注意书写std,C++的命令需要std,例如std::cout,std::cin,std::string



### 2.7 bool类型

>**作用**：表示真假
>
>bool类型只有两个值：
>
>​				true:1
>
>​				false:0
>
>>+ 任何非0整数都是1；
>>+ 输入字符是假
>
>bool类型只占用一个字节
>
>```c++
>#include<iostream>
>#include<string>
>
>int main()
>{
>	
>	bool flag = true;
>	std::cout<<flag<<" " << sizeof(flag) << std::endl;
>	flag = false;
>	std::cout << flag << " " << sizeof(flag) << std::endl;
>	system("pause");
>	return 0;
>```
>
>

### 2.8数据的输入

>**作用**：从键盘获取数据
>
>用法：std::cin >> ;
>
>```c++
>#include<iostream>
>#include<string>
>
>int main()
>{
>	
>	//整型
>	int a;
>	std::cout << "输入a的值:" ;
>	std::cin >> a;
>	std::cout << a << std::endl;
>	//浮点型
>	float f;
>	std::cout << "输入f的值:";
>	std::cin >> f;
>	std::cout << f << std::endl;
>	//字符型
>	char ch;
>	std::cout << "请输入ch的值";
>	std::cin >> ch;
>	std::cout << ch << std::endl;
>	//字符串
>	std::string str;
>	std::cout << "请输入str的值";
>	std::cin >> str;
>	std::cout << str << std::endl;
>	//bool型
>	bool flag;
>	std::cout << "请输入flag的值：";
>	std::cin >> flag;
>	std::cout << flag << std::endl;
>
>	system("pause");
>	return 0;
>}
>```
>
>

## 3 运算符



### 3.1算数运算符

>**作用**：用于四则运算

| **运算符** | **术语**   | **示例**    | **结果**  |
| ---------- | ---------- | ----------- | --------- |
| +          | 正号       | +3          | 3         |
| -          | 负号       | -3          | -3        |
| +          | 加         | 10 + 5      | 15        |
| -          | 减         | 10 - 5      | 5         |
| *          | 乘         | 10 * 5      | 50        |
| /          | 除         | 10 / 5      | 2         |
| %          | 取模(取余) | 10 % 3      | 1         |
| ++         | 前置递增   | a=2; b=++a; | a=3; b=3; |
| ++         | 后置递增   | a=2; b=a++; | a=3; b=2; |
| --         | 前置递减   | a=2; b=--a; | a=1; b=1; |
| --         | 后置递减   | a=2; b=a--; | a=1; b=2; |

>```c++
>//加减乘除
>int main() {
>
>	int a1 = 10;
>	int b1 = 3;
>
>	cout << a1 + b1 << endl;
>	cout << a1 - b1 << endl;
>	cout << a1 * b1 << endl;
>	cout << a1 / b1 << endl;  //两个整数相除结果依然是整数
>
>	int a2 = 10;
>	int b2 = 20;
>	cout << a2 / b2 << endl; 
>
>	int a3 = 10;
>	int b3 = 0;
>	//cout << a3 / b3 << endl; //报错，除数不可以为0
>
>
>	//两个小数可以相除
>	double d1 = 0.5;
>	double d2 = 0.25;
>	cout << d1 / d2 << endl;
>
>	system("pause");
>
>	return 0;
>}
>```
>
>>除法注意点：
>>
>>+ 整型进行除法，结果会直接舍掉小数位
>
>```c++
>//取模运算
>#include<iostream>
>#include<string>
>int main()
>{
>	int a1 = 10;
>	std::cout << a1 % 3 << std::endl;
>	system("pause");
>	return 0;
>}
>```
>
>>+ 取模运算就是求余数
>>+ 两个数取模是基于除法，所以被除数不能为0
>>+ 小数不能进行取模运算
>
>```c++
>//递增和递减运算符
>
>```
>
>

### 3.2 赋值运算符

>**作用：**给变量赋值

| **运算符** | **术语** | **示例**   | **结果**  |
| ---------- | -------- | ---------- | --------- |
| =          | 赋值     | a=2; b=3;  | a=2; b=3; |
| +=         | 加等于   | a=0; a+=2; | a=2;      |
| -=         | 减等于   | a=5; a-=3; | a=2;      |
| *=         | 乘等于   | a=2; a*=2; | a=4;      |
| /=         | 除等于   | a=4; a/=2; | a=2;      |
| %=         | 模等于   | a=3; a%2;  | a=1;      |

>int main() {
>
>```c++
>//赋值运算符
>
>// =
>int a = 10;
>a = 100;
>cout << "a = " << a << endl;
>
>// +=
>a = 10;
>a += 2; // a = a + 2;
>cout << "a = " << a << endl;
>
>// -=
>a = 10;
>a -= 2; // a = a - 2
>cout << "a = " << a << endl;
>
>// *=
>a = 10;
>a *= 2; // a = a * 2
>cout << "a = " << a << endl;
>
>// /=
>a = 10;
>a /= 2;  // a = a / 2;
>cout << "a = " << a << endl;
>
>// %=
>a = 10;
>a %= 2;  // a = a % 2;
>cout << "a = " << a << endl;
>
>system("pause");
>
>return 0;
>```
>}
>
>

### 3.3比较运算符

>**作用**：用于表达式之间的比较，返回一个真或假的值

| **运算符** | **术语** | **示例** | **结果** |
| ---------- | -------- | -------- | -------- |
| ==         | 相等于   | 4 == 3   | 0        |
| !=         | 不等于   | 4 != 3   | 1        |
| <          | 小于     | 4 < 3    | 0        |
| \>         | 大于     | 4 > 3    | 1        |
| <=         | 小于等于 | 4 <= 3   | 0        |
| \>=        | 大于等于 | 4 >= 1   | 1        |

>```c++
>int main() {
>
>	int a = 10;
>	int b = 20;
>
>	cout << (a == b) << endl; // 0 
>
>	cout << (a != b) << endl; // 1
>
>	cout << (a > b) << endl; // 0
>
>	cout << (a < b) << endl; // 1
>
>	cout << (a >= b) << endl; // 0
>
>	cout << (a <= b) << endl; // 1
>	
>	system("pause");
>
>	return 0;
>}
>```



### 3.4逻辑运算符

>**作用**：根据表达式的值返回真值或假值

| **运算符** | **术语** | **示例** | **结果**                                                 |
| ---------- | -------- | -------- | -------------------------------------------------------- |
| !          | 非       | !a       | 如果a为假，则!a为真；  如果a为真，则!a为假。             |
| &&         | 与       | a && b   | 如果a和b都为真，则结果为真，否则为假。                   |
| \|\|       | 或       | a \|\| b | 如果a和b有一个为真，则结果为真，二者都为假时，结果为假。 |

>```c++
>//逻辑运算符  --- 非
>int main() {
>
>	int a = 10;
>
>	cout << !a << endl; // 0
>
>	cout << !!a << endl; // 1
>
>	system("pause");
>
>	return 0;
>}
>```
>
>
>
>```C++
>//逻辑运算符  --- 与
>int main() {
>
>	int a = 10;
>	int b = 10;
>
>	cout << (a && b) << endl;// 1
>
>	a = 10;
>	b = 0;
>
>	cout << (a && b) << endl;// 0 
>
>	a = 0;
>	b = 0;
>
>	cout << (a && b) << endl;// 0
>
>	system("pause");
>
>	return 0;
>}
>```
>
>```c++
>//逻辑运算符  --- 或
>int main() {
>
>	int a = 10;
>	int b = 10;
>
>	cout << (a || b) << endl;// 1
>
>	a = 10;
>	b = 0;
>
>	cout << (a || b) << endl;// 1 
>
>	a = 0;
>	b = 0;
>
>	cout << (a || b) << endl;// 0
>
>	system("pause");
>
>	return 0;
>}
>```
>
>

