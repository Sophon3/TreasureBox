# 黑马程序员

## 1 C++初识

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



## 2 数据类型

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



## 4 程序流程结构

> C/C++支持最基本的三种程序运行结构：顺序结构、选择结构、循环结构
> +顺序结构：程序按顺序执行，不发生跳转
> +选择结构：判断条件是否满足，选择对应的程序执行
> +循环结构：判断条件是否满足，多次循环执行某一段代码

### 4.1 选择结构

#### 1.if结构

>if语句
>
>1:if
>
>2:if...else
>
>3:if...else if
>
>```c++
>//单if语句
>#include<iostream>
>#include<string>//string类型
>
>int main() {
>
>	int score;
>	std::cout << "输入你的分数:";
>	std::cin >> score;
>	if (score > 600)
>	{
>		std::cout << "一本大学"<<std::endl;
>	}
>	system("pause");
>	return 0;
>}
>```
>
>
>
>```c++
>//if...else结构
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int main() {
>
>	int score;
>	std::cout << "输入你的分数:";
>	std::cin >> score;
>	if (score > 600)
>	{
>		std::cout << "一本"<<std::endl;
>	}
>	else
>	{
>		std::cout << "没有考上一本大学" << std::endl;
>	}
>
>	system("pause");
>
>	return 0;
>}
>```
>
>
>
>```c++
>//if...else if结构
>#include<iostream>
>#include<string>//string类型需要该头文件
>int main() {
>
>	int score;
>	std::cout << "输入你的分数:";
>	std::cin >> score;
>	if (score > 700)
>	{
>		std::cout << "清华"<<std::endl;
>	}
>	else if(score>600)
>	{
>		std::cout << "一本" << std::endl;
>	}
>	else
>	{
>		std::cout << "没有考上一本" << std::endl;
>	}
>
>	system("pause");
>
>	return 0;
>}
>```
>
>
>
>```c++
>//if嵌套
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int main() {
>
>	int score;
>	std::cout << "输入你的分数:";
>	std::cin >> score;
>	if (score > 600)
>	{
>		if (score > 700)
>		{
>			std::cout << "清华" << std::endl;
>		}
>		else
>		{
>			std::cout << "普通一本"<<std::endl;
>		}
>	}
>	else if(score>500)
>	{
>		std::cout << "二本" << std::endl;
>	}
>	else if (score > 400)
>	{
>		std::cout<<"三本"<<std::endl;
>	}
>	else
>	{
>		std::cout << "未考上本科" << std::endl;
>	}
>
>	system("pause");
>
>	return 0;
>}
>```

#### 2.案例练习 三只小猪称体重

有三只小猪ABC，请分别输入三只小猪的体重，并且判断哪只小猪最重？![](https://cdn.jsdelivr.net/gh/Sophon3/Figure-bed/images2021/2021202110281311989.png)

```c++
#include<iostream>
#include<string>//string类型需要该头文件

int main() 
{
	float pig1, pig2,pig3;
	std::cout << "输入三只小猪的重量" << std::endl;
	std::cout << "please input the pig1 weight:";
	std::cin >> pig1;
	std::cout << "please input the pig2 weight:";
	std::cin >> pig2;
	std::cout << "please input the pig3 weight:";
	std::cin >> pig3;
	if(pig1 > pig2)
	{
		if (pig1 > pig3)
		{
			std::cout << "pig1 is  the heaviest" << std::endl;
		}
		else
		{
			std::cout << "pig2 is the heaviest" << std::endl;
		}
	}
	else
	{
		if (pig2 > pig3)
		{
			std::cout << "pig2 is the heavest" << std::endl;
		}
		else
		{
			std::cout << "pig3 is the  heavest" << std::endl;
		}
	}
	system("pause");

	return 0;
}
```

#### 3.三目运算符

>**作用：** 通过三目运算符实现简单的判断
>
>**语法：**`表达式1 ? 表达式2 ：表达式3`
>
>**例子**：a > b ? a:b
>
>如果a大于b,返回a,否则返回b
>
>```c++
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int main() 
>{
>	int a = 10;
>	int b = 20;
>	int c;
>	c = (a > b ? a : b);
>	//三目运算符返回的是一个变量，接下来还能继续赋值
>	std::cout<<"c的值：" << c << std::endl;
>	system("pause");
>	return 0;
>}
>```
>



### 4.switch语句

>**作用**：执行多条件分支语句
>
>**语法**：
>
>```c++
>switch(表达式)
>{
>    case 结果1 :执行语句1;break;
>    case 结果2 :执行语句1;break;
>    case 结果3 :执行语句1;break;
>        .
>        .
>        .
>    default: 执行语句;break;
>}
>```
>
>**例子**
>
>```c++
>//switch
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int main() 
>{
>	std::cout << "请给电影打分(0-10):";
>	int score;
>	std::cin >> score;
>	std::cout << "这个电影的分数是：" << score << std::endl;
>	switch (score)
>	{
>	case 0:
>	case 1:
>	case 2:
>	case 3:
>		std::cout << "烂片" << std::endl; break;//退出当前分支
>	case 4:
>	case 5:
>	case 6:
>	case 7:
>		std::cout << "还行" << std::endl; break;
>	case 8:
>		std::cout << "好看" << std::endl; break;
>	case 9:
>	case 10:
>		std::cout << "经典" << std::endl; break;
>	default:
>		std::cout << "error" << std::endl; break;
>
>	}
>
>```
>
>>if和siwtch区别
>>
>>+ if能判断范围
>>+ switch结构更加清晰
>>+ switch效率更高
>
>>**注意**:
>>
>>+ switch的表达式类型只能是整型或者字符型

### 4.2 循环结构

#### 1.while循环语句

>**作用**：满足循环条件，执行循环语句
>
>**语法**：`while (条件) {循环语句}`
>
>```c++
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int main() 
>{
>	int num = 0;
>	std::cout << num << std::endl;
>	num++;
>	std::cout << num << std::endl;
>	while (num < 10)
>	{
>		num++;
>	}
>	std::cout << num << std::endl;
>	return 0;
>	system("pause");
>}
>```
>
>>while循环需要提供一个循环出口，避免进入死循环

##### 案例：猜数字

>>**案例描述：**系统随机生成一个1到100之间的数字，玩家进行猜测，如果猜错，提示玩家数字过大或过小，如果猜对恭喜玩家胜利，并且退出游戏。
>
>```c++
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int main() 
>{
>	//生成随机数
>	int num = rand() % 100 + 1;
>	std::cout << "随机数猜测" << std::endl;
>	int val=0;
>	while (val != num) //方式1，直接在while中添加循环条件
>	{
>		std::cout << "请输入你的猜测：";
>		std::cin >> val;
>		if (val < num)
>		{
>			std::cout << "你猜测的过小了" << std::endl;
>		}
>		else if (val == num)
>		{
>			std::cout << "你猜对了" << std::endl;
>		}
>		else if (val > num)
>		{
>			std::cout << "你猜测的过大了" << std::endl;
>		}
>	}
>	return 0;
>	system("pause");
>}
>/*
>*******************************************
>方式2
>	while (1) //方式2,使用while死循环开始，在循环之中添加break;可退出循环
>	
>	{
>		std::cout << "请输入你的猜测：";
>		std::cin >> val;
>		if (val < num)
>		{
>			std::cout << "你猜测的过小了" << std::endl;
>		}
>		else if (val == num)
>		{
>			std::cout << "你猜对了" << std::endl;
>			break;
>		}
>		else if (val > num)
>		{
>			std::cout << "你猜测的过大了" << std::endl;
>		}
>********************************************
>*/
>```
>
>>生成随机数
>>
>>rand()%100  //这个可以生成一个随机数，但是是伪随机，所以每次生成的随机数都是41
>>
>>这个时候可以添加一个随机数种子，利用系统时间来生成随机数，防止每一次随机数都一样
>>
>>srand((unsigned int)time(NULL))
>>
>>使用这个需要包含一个系统时间头文件#include<ctime>。
>>
>>`srand((unsigned int)time(NULL));
>>	int num = rand() % 100 + 1;`

#### 2. do...while循环语句

>**作用**：与while相同，只是先执行一次循环
>
>```c++
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int main() 
>{
>	int num = 0;
>	do
>	{
>		std::cout << num << std::endl;
>		num++;
>	} 
>	while (num <10);
>	return 0;
>	system("pause");
>}
>```
>
>



##### 案例练习 ：水仙花数

>**案例描述：**水仙花数是指一个 3 位数，它的每个位上的数字的 3次幂之和等于它本身
>
>例如：1^3 + 5^3+ 3^3 = 153
>
>请利用do...while语句，求出所有3位数中的水仙花数
>
>```c++
>#include<iostream>
>#include<cmath>
>
>int main() 
>{
>	int num = 100;
>	do
>	{
>		int a, b, c;
>		a = num % 10;//取个位
>		b = num / 10 % 10;//取十位
>		c = num / 100;//取百位
>		if ( pow(a,3) + pow(b, 3) + pow(c, 3) == num)
>		{
>			std::cout << num << std::endl;
>		}
>		num++;
>	} while (num < 1000);
>
>	return 0;
>	system("pause");
>}
>```
>
>> 求指数函数：pow(底数，指数)//需要包含cmath头文件。

#### 3. for循环结构

>**作用**：满足循环条件，执行循环语句
>
>**语法**：for(起始表达式;条件表达式;末尾循环体){循环语句}
>
>```c++
>#include<iostream>
>#include<string>//string类型需要该头文件
>#include<cmath>
>
>int main() 
>{
>	int num=0;
>	for (int i = 0; i < 10; i++)
>	{
>		std::cout << num << std::endl;
>		num++;
>	}
>	return 0;
>	system("pause");
>}
>```
>
>

##### 案例练习：敲桌子

>案例描述：从1开始数到数字100， 如果数字个位含有7，或者数字十位含有7，或者该数字是7的倍数，我们打印敲桌子，其余数字直接打印输出。
>
>```c++
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int main() 
>{
>	int a, b;
>	for (int i = 1; i <= 100; i++)
>	{
>		if (i % 10 == 7 || i / 10 % 10 == 7 || i % 7 == 0)//条件判断
>		{
>			std::cout << "敲桌子" << std::endl;
>		}
>		else
>		{
>			std::cout << i << std::endl;
>		}
>	}
>	return 0;
>	system("pause");
>}
>
>```
>
>

#### 4.嵌套循环

>**作用：** 在循环体中再嵌套一层循环，解决一些实际问题
>
>```c++
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int main() 
>{
>	for (int i = 0; i < 10; i++)
>	{
>		for (int j = 0; j < 10; j++)
>		{
>			std::cout << "* ";
>		}
>		std::cout << std::endl;
>
>	}
>	return 0;
>	system("pause");
>}
>```
>
>
>
>

##### 案例练习

>案例描述：利用嵌套循环，实现九九乘法表
>
>```c++
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int main() 
>{
>	for (int i = 1; i < 10; i++)
>	{
>		for (int j = 1; j<=i; j++)
>		{
>			std::cout << i << "x" << j << " = " << i * j <<"  ";
>		}
>		std::cout << std::endl;
>		std::cout << std::endl;
>
>	}
>	return 0;
>	system("pause");
>}
>```
>
>

### 4.3 跳转语句

#### 1. break语句

>> 作用:跳出 选择结构 或 循环结构 
>
>+ 跳出switch语句
>+ 结束循环语句
>+ 当有多层循环时，结束内层循环
>

#### 2. continue语句

>**作用**：在一个循环语句中，结束本次循环，继续后面的循环
>
>```c++
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int main() 
>{
>	for (int i = 0; i < 100; i++)
>	{
>		if (i % 2 == 0)
>		{
>			continue;
>		}
>		else 
>		{
>			std::cout << i << std::endl;
>		}
>	}
>	return 0;
>	system("pause");
>}
>```



#### 3.goto语句

>**作用：**可以无条件跳转语句  (汇编的标识）//尽量少使用
>
>**语法：** `goto 标记;`
>
>**解释：**如果标记的名称存在，执行到goto语句时，会跳转到标记的位置
>
>```c++
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int main() 
>{
>	std::cout << "1" << std::endl;
>
>	goto FLAG;
>
>	std::cout << "2" << std::endl;
>	std::cout << "3" << std::endl;
>	std::cout << "4" << std::endl;
>
>FLAG:
>
>	std::cout << "5" << std::endl;
>	return 0;
>	system("pause");
>}
>```
>
>

## 5 数组（Array）

>所谓数组，就是一个集合，里面存放了相同类型的数据元素
>
>**特点1：**数组中的每个==数据元素都是相同的数据类型==
>
>**特点2：**数组是由==连续的内存==位置组成的

### 5.1一维数组

#### 1.1 一维数组定义方式

>#### 三种定义方式：
>
>1. ` 数据类型  数组名[ 数组长度 ]; `
>2. `数据类型  数组名[ 数组长度 ] = { 值1，值2 ...};`
>3. `数据类型  数组名[ ] = { 值1，值2 ...};`
>
>```c++
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int main() 
>{
>	int arr1[10];
>	arr1[0] = 90;
>	arr1[2] = 80;
>	for (int i = 0; i < 10; i++)
>	{
>		std::cout << "arr1第" << i << "个：" << arr1[i] << std::endl;
>	}
>	int arr2[10] = {10,20,30,40,50,60,70,80,90,100};
>	for (int i = 0; i < 10; i++)
>	{
>		std::cout <<"arr2第"<<i<<"个：" << arr2[i] << std::endl;
>	}
>	int arr3[] = {20,30,40,50,60,70,80,90,100 };
>	for (int i = 0; i < 10; i++)
>	{
>		std::cout << "arr3第" << i << "个：" << arr3[i] << std::endl;
>	}
>	return 0;
>	system("pause");
>}
>```
>
>>注意int数组没有赋初值,打印出来会是-858993460,具体[可见](https://blog.csdn.net/huijiaaa1/article/details/89361230),这个涉及编译器和汇编
>>
>>+ 定义数组的时候，必须定义数组的长度，可以直接定义长度，也能通过赋值方式让系统自动伪他定义长度。
>

#### 1.2一维数组组名

>一维数组名称的**用途**：
>
>1. 可以统计整个数组在内存中的长度
>2. 可以获取数组在内存中的首地址
>
>```c++
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int main() 
>{
>	int arr[5] = { 1,12,123,1234,12345 };
>	std::cout << arr << std::endl;//查看数组首地址
>	std::cout << sizeof(arr) << std::endl;//整个数组占用的内存空间
>	std::cout << sizeof(arr[0]) << std::endl;//查看数组某个单元占用的内存
>	std::cout << sizeof(arr) / sizeof(arr[0]) << std::endl;
>
>	std::cout << "数组首地址为： " << (int)arr << std::endl;//查看首地址，int为10进制
>	std::cout << "数组中第一个元素地址为： " << (int)&arr[0] << std::endl;
>	std::cout << "数组中第二个元素地址为： " << (int)&arr[1] << std::endl;
>
>	return 0;
>	system("pause");
>}
>```
>
>>数组首地址是一个常量，不可修改

##### 案例练习 1.五只小猪称体重

>**案例描述：**
>
>在一个数组中记录了五只小猪的体重，如：int arr[5] = {300,350,200,400,250};
>
>找出并打印最重的小猪体重。
>
>```c++
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int main() 
>{
>	int arr[5] = { 300,350,200,400,250 };
>	int arr_length = sizeof(arr) / sizeof(arr[1]);
>	int max = 0;
>	int ser;
>	for (int i = 0; i < arr_length; i++)
>	{
>		if(arr[i]>max)
>		{
>			max = arr[i];
>			ser = i+1;
>		}
>		
>	}
>	std::cout<<"第"<<ser<< "只小猪最重，为：" << max;
>	return 0;
>	system("pause");
>}
>```

案例练习 2.数组元素逆置

>**案例描述：**请声明一个5个元素的数组，并且将元素逆置.               
>
>(如原数组元素为：1,3,2,5,4;逆置后输出结果为:4,5,2,3,1);
>
>```c++
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int main() 
>{
>	int arr[7] = { 1,2,3,4,5,6,7};
>	int arr_length = sizeof(arr) / sizeof(arr[1]);
>	int arr_end = arr_length-1;
>	int temp;
>	for (int i = 0; i <arr_end; i++)
>	{
>		temp = arr[i];
>		arr[i] = arr[arr_end];
>		arr[arr_end] = temp;
>		arr_end--;
>	}
>	for (int i = 0; i < arr_length; i++)
>	{
>		std::cout << arr[i]<<std::endl;
>	}
>	return 0;
>	system("pause");
>}
>```
>
>>关注点数组前后置换过程种，

#### 1.3冒泡排序

>**作用：** 最常用的排序算法，对数组内元素进行排序
>
>1. 比较相邻的元素。如果第一个比第二个大，就交换他们两个。
>2. 对每一对相邻元素做同样的工作，执行完毕后，找到第一个最大值。
>3. 重复以上的步骤，每次比较次数-1，直到不需要比较
>
>>**示例：** 将数组 { 4,2,8,0,5,7,1,3,9 } 进行升序排序
>
>```c++
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int main() 
>{
>	int arr[] = { 4,2,12,0,5,11,1,3,9 };
>	int arr_len = sizeof(arr) / sizeof(arr[1]);
>	int temp;//中转数
>	for (int i = 0; i < arr_len-1; i++)//循环数组长度-1
>	{
>		for (int j = 0; j < arr_len -i-1 ; j++)//比较次数为数组长度-1-已循环次数
>		{
>			if (arr[j] > arr[j+1])
>			{
>				temp = arr[j];   //数组相联两数交换
>				arr[j] = arr[j+1];
>				arr[j+1] = temp;
>			}
>		}
>	}
>	for (int i = 0; i < arr_len; i++)//打印数组
>	{
>		std::cout << arr[i] << std::endl;
>	}
>	return 0;
>	system("pause");
>}
>```
>
>

### 5.2二维数组

#### 2.1二维数组定义方式

>1. ` 数据类型  数组名[ 行数 ][ 列数 ]; `
>2. `数据类型  数组名[ 行数 ][ 列数 ] = { {数据1，数据2 } ，{数据3，数据4 } };`
>3. `数据类型  数组名[ 行数 ][ 列数 ] = { 数据1，数据2，数据3，数据4};`
>4. ` 数据类型  数组名[  ][ 列数 ] = { 数据1，数据2，数据3，数据4};`
>
>```c++
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int main() 
>{
>	int arr1[2][3];
>	arr1[0][0] = 1;
>	arr1[0][1] = 2;
>	arr1[0][2] = 3;
>	arr1[1][0] = 4;
>	arr1[1][1] = 5;
>	arr1[1][2] = 6;
>	for (int i = 0; i < 2; i++)
>	{
>		for (int j = 0; j < 3;j++)
>		{
>			std::cout << arr1[i][j]<<" ";
>		}
>		std::cout << std::endl;
>	}
>	std::cout << std::endl;
>	int arr2[2][3] =
>	{
>		{1,2,4},
>		{4,3,2}
>	};
>	for (int i = 0; i < 2; i++)
>	{
>		for (int j = 0; j < 3; j++)
>		{
>			std::cout << arr2[i][j] << " ";
>		}
>		std::cout << std::endl;
>	}
>	std::cout << std::endl;
>	int arr3[2][3] = { 3,4,3,4,1,6 };
>	for (int i = 0; i < 2; i++)
>	{
>		for (int j = 0; j < 3; j++)
>		{
>			std::cout << arr3[i][j] << " ";
>		}
>		std::cout << std::endl;
>	}
>	int arr4[][3] = { 1,2,5,3,2,7 };//可以给出列数，省略函数，系统能自动判断。
>
>	return 0;
>	system("pause");
>}
>```
>
>>方式而最常用，也最直观，可读性更强。

#### 2.2 二维数组名

>* 查看二维数组所占内存空间
>* 获取二维数组首地址
>
>```c++
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int main()
>{
>	int arr[2][3] =
>	{
>		{1,2,4},
>		{4,3,2}
>	};
>	std::cout << "首地址" << arr << std::endl;
>	std::cout << "数组大小" << sizeof(arr) << std::endl;
>	std::cout << "一行占用内存" << sizeof(arr[0]) << std::endl;
>	std::cout << "某个元素占用内存" << sizeof(arr[0][0]) << std::endl;
>	std::cout << "二维数组行数" << sizeof(arr) / sizeof(arr[0]) << std::endl;
>	std::cout << "二维数组列数" << sizeof(arr[0]) / sizeof(arr[0][0]) << std::endl;
>	std::cout << "二维数组第一个元素地址：" << &arr[0][0] << std::endl;
>	std::cout << "二维数组第二个元素地址：" << &arr[0][1] << std::endl;
>	return 0;
>	system("pause");
>}
>```

##### 案例练习

>**考试成绩统计：**
>
>案例描述：有三名同学（张三，李四，王五），在一次考试中的成绩分别如下表，**请分别输出三名同学的总成绩**
>
>|      | 语文 | 数学 | 英语 |
>| ---- | ---- | ---- | ---- |
>| 张三 | 100  | 100  | 100  |
>| 李四 | 90   | 50   | 100  |
>| 王五 | 60   | 70   | 80   |
>
>```c++
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int main()
>{
>	int scores[3][3] =
>	{
>		{100,100,100},
>		{90,50,100},
>		{60,70,80}
>	};
>	int num = 0;
>	std::string names[3] = { "张三","李四","王五" };
>	std::string subject[3] = {"语文","数学","英语"};
>	for (int i = 0; i< 3; i++)
>	{
>		for (int j = 0; j < 3; j++)
>		{
>			std::cout << names[i] << subject[j] << "成绩" << scores[i][j] << std::endl;
>			num +=scores[i][j];
>		}
>		std::cout << names[i] << "总分:" << num << std::endl << std::endl;
>		num = 0;
>	}
>	return 0;
>	system("pause");
>}
>```
>
>





## 6 函数

### 6.1概述

>**作用：**将一段经常使用的代码封装起来，减少重复代码
>
>一个较大的程序，一般分为若干个程序块，每个模块实现特定的功能。

### 6.2函数的定义

>##### 第一函数的步骤：
>
>1. 返回值类型 (一个函数可以返回一个值，在函数定义中)
>2. 函数名 (给函数起一个名字)
>3. 参数列表 (使用该函数时，传入的数据)
>4. 函数体语句 (花括号内的代码，该函数内需要执行的语句)
>5. return 表达式 (返一个值，返回值的类型与函数定义的返回值类型有关)
>
>```c++
>返回值类型 函数名 （参数列表）
>{
>
>      函数体语句
>
>      return表达式
>
>}
>```
>
>```c++
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int add(int, int);//函数声明
>
>int main()
>{
>	int a = 10;
>	int b = 20;
>	int c = add(a, b);//函数调用，a和b为实参
>	std::cout << c << std::endl;
>	return 0;
>	system("pause");
>}
>
>int add(int num1, int num2)//函数定义,num1和num2为形参
>{
>	int sum;
>	sum = num1 + num2;
>	return sum;
>}
>```
>
>

### 6.3函数的调用

>能：**使用定义好的函数
>
>**语法：**` 函数名（参数）`
>
>```c++
>同上
>```
>
>



### 6.4值传递

>* 所谓值传递，就是函数调用时实参将数值传入给形参
>* 值传递时，==如果形参发生，并不会影响实参==
>
>```c++
>#include<iostream>
>#include<string>//string类型需要该头文件
>
>int swap(int, int);
>
>int main()
>{
>	int a = 10;
>	int b = 20;
>	swap(a, b);
>	std::cout << "main中a的值" << a << std::endl;
>	std::cout << "main中b的值" << b << std::endl;
>	return 0;
>	system("pause");
>}
>
>int swap(int num1, int num2)
>{
>	int temp;
>	temp = num1;
>	num1 = num2;
>	num2 = temp;
>	std::cout << "swap中a的值" << num1 << std::endl;
>	std::cout << "swap中b的值" << num2 << std::endl;
>	return 0;
>
>}
>```
>
>

### 6.5 函数常见的样式

>常见的函数样式有4种
>
>1. 无参无返
>2. 有参无返
>3. 无参有返
>4. 有参有返
>
>```c++
>//函数常见样式
>//1、 无参无返
>void test01()
>{
>	//void a = 10; //无类型不可以创建变量,原因无法分配内存
>	cout << "this is test01" << endl;
>	//test01(); 函数调用
>}
>
>//2、 有参无返
>void test02(int a)
>{
>	cout << "this is test02" << endl;
>	cout << "a = " << a << endl;
>}
>
>//3、无参有返
>int test03()
>{
>	cout << "this is test03 " << endl;
>	return 10;
>}
>
>//4、有参有返
>int test04(int a, int b)
>{
>	cout << "this is test04 " << endl;
>	int sum = a + b;
>	return sum;
>}
>```
>
>

### 6.6函数的声明

>**作用：** 告诉编译器函数名称及如何调用函数。函数的实际主体可以单独定义。
>
>
>
>*  函数的**声明可以多次**，但是函数的**定义只能有一次**
>
>```c++
>//声明可以多次，定义只能一次
>//声明
>int max(int a, int b);
>int max(int a, int b);
>//定义
>int max(int a, int b)
>{
>	return a > b ? a : b;
>}
>
>int main() {
>
>	int a = 100;
>	int b = 200;
>
>	cout << max(a, b) << endl;
>
>	system("pause");
>
>	return 0;
>}
>```



### 6.7函数分文件编写

>**作用：**让代码结构更加清晰
>
>函数分文件编写一般有4个步骤
>
>1. 创建后缀名为.h的头文件  
>2. 创建后缀名为.cpp的源文件
>3. 在头文件中写函数的声明
>4. 在源文件中写函数的定义
>
>```c++
>//swap.h
>#include<iostream>
>#include<string>//string类型需要该头文件
>void swap(int, int);
>
>```
>
>```c++
>//swap.cpp
>#include"swap.h"
>
>void swap(int num1, int num2)
>{
>	int temp;
>	temp = num1;
>	num1 = num2;
>	num2 = temp;
>	std::cout << "swap中a的值" << num1 << std::endl;
>	std::cout << "swap中b的值" << num2 << std::endl;
>}
>```
>
>```c++
>//main.cpp
>#include"swap.h"
>
>int main()
>{
>	int a = 10;
>	int b = 20;
>	std::cout << "main中a的值" << a << std::endl;
>	std::cout << "main中b的值" << b << std::endl;
>	swap(a, b);
>	return 0;
>	system("pause");
>}
>
>
>```



## 7 指针

### 7.1指针的概念

>**指针的作用
>
>**：** 可以通过指针间接访问***内存***
>
>* 内存编号是从0开始记录的，一般用十六进制数字表示
>* 可以利用指针变量保存地址
>
>

### 7.2指针变量的定义和使用

>指针变量定义语法： `数据类型 * 变量名；`
>
>```c++
>#include<iostream>
>
>int main()
>{
>	int a = 10;
>	int* p;
>	p = &a;
>	std::cout << &a << std::endl;
>	std::cout << p << std::endl;
>	return 0;
>	system("pause");
>}
>
>
>```
>
>>#### 普通变量和指针变量的区别
>>
>>+ 普通变量存放的是数据，指针变量存储的是地址
>>+ 指针变量可以通过 * 操作数，操作指针变量指向的内存空间，这个过程称为引用
>
>>+ 通过&符号 获取变量的地址
>>+ 指针可以记录地址
>>+ 对指针变量解引用，可以操作指针指向的内存
>>+ 
>>
>>

