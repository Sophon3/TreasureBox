### 7.3 指针所占内存空间

>指针这种数据结构所占用的内存空间
>
>
>
>```c++
>#include<iostream>
>
>int main()
>{
>	int a = 10;
>
>	int* p;
>	p = &a; //指针指向数据a的地址
>
>	std::cout << *p << std::endl; //* 解引用
>	std::cout << sizeof(p) << std::endl;
>	std::cout << sizeof(char*) << std::endl;
>	std::cout << sizeof(float*) << std::endl;
>	std::cout << sizeof(double*) << std::endl;
>	return 0;
>	system("pause");
>}
>
>
>```
>
>x86 
>
>![](https://cdn.jsdelivr.net/gh/Sophon3/Figure-bed/images2021/2021202111011115825.png)
>
>x64
>
>![](https://cdn.jsdelivr.net/gh/Sophon3/Figure-bed/images2021/2021202111011114060.png)
>
>指针类型在64位系统中占用8字节，在32位系统中，占4字节
>
>

### 7.4空指针和野指针

>**空指针**：指针变量指向内存中编号为0的空间
>
>**用途：**初始化指针变量
>
>**注意：**空指针指向的内存是不可以访问的
>
>```c++
>#include<iostream>
>
>int main()
>{
>	int a = 10;
>
>	int* p = NULL;
>	std::cout << *p;
>	return 0;
>	system("pause");
>}
>
>```
>
>空指针不能被访问，会报错
>
>![image-20211101112618582](C:\Users\Quer\AppData\Roaming\Typora\typora-user-images\image-20211101112618582.png)
>
> 
>
>**野指针**：指针变量指向非法的内存空间
>
>```c++
>int main() {
>
>	//指针变量p指向内存地址编号为0x1100的空间
>	int * p = (int *)0x1100;
>
>	//访问野指针报错 
>	cout << *p << endl;
>
>	system("pause");
>
>	return 0;
>}
>```
>
>



### 7.5 const修饰指针

>1. const修饰指针   --- 常量指针
>2. const修饰常量   --- 指针常量
>3. const即修饰指针，又修饰常量
>
>```c++
>#include<iostream>
>
>int main()
>{
>	int a = 10;
>	int b = 20;
>	const int* p = &a;//指针常量,指针指向的值不能修改，指针的指向可以修改
>	// *p = 20;  错误，指针指向的值不能修改
>	p = &b;//正确，指针的指向可以修改。
>
>	int* const p2 = &a;//指针常量，指针指向的值可以修改，但是指针的指向不能修改
>	*p2 = 20;//正确，指针指向的值可以修改
>	//p2 = &b;  //错误，指针的指向不能修改
>
>	const int* const p3 = &a;//此时指针的指向和指向的值都不能修改
>	system("pause");
>}
>
>
>```
>
>



### 7.6指针和数组

>**作用：**利用指针访问数组中元素
>
>```c++
>#include<iostream>
>
>int main()
>{
>	int arr[10] = { 1,2,3,4,5,6,7,8,9,10 };
>	int* p = arr;//数组名就是数组的首地址
>	std::cout << "第一个元素为：" << *p << std::endl;
>	p++;
>	std::cout << "下一个元素为：" << *p << std::endl;
>
>	system("pause");
>	return 0;
>}
>
>```
>
>

### 7.7指针和函数

>**作用：**利用指针作函数参数，可以修改实参的值
>
>```c++
>#include<iostream>
>
>void swap(int*, int*);
>
>int main()
>{
>	int a = 10;
>	int b = 20;
>	std::cout << "a的值为：" << a << " ,b的值为：" << b << std::endl;
>	swap(&a, &b);//地址传递
>	std::cout << "a的值为：" << a << " ,b的值为：" << b << std::endl;
>	system("pause");
>	return 0;
>}
>
>void swap(int* p1, int* p2)//通过接收原变量的地址，可以修改main函数的值
>{
>	int temp = *p1;
>	*p1 = *p2;
>	*p2 = temp;
>}
>
>```
>
>

### 7.8 指针、数组、函数

>**案例描述：**封装一个函数，利用冒泡排序，实现对整型数组的升序排序
>
>例如数组：int arr[10] = { 4,3,6,9,1,2,10,8,7,5 };
>
>```c++
>#include<iostream>
>void BubbleSort(int*, int);
>void Display_arr(int*, int);
>
>int main()
>{
>	int arr[10] = { 4,3,6,9,1,2,10,8,7,5 };
>	int arr_len = sizeof(arr) / sizeof(arr[0]);
>	Display_arr(arr, arr_len);
>	BubbleSort(arr, arr_len);
>	Display_arr(arr, arr_len);
>	system("pause");
>	return 0;
>}
>
>void BubbleSort(int* arr, int len)
>{
>	int i = 0;
>	int j = 0;
>	int temp;
>	for (i = 0; i < len - 1; i++)
>	{
>		for (j = 0; j < len - 1 - i; j++)
>		{
>			if (arr[j] > arr[j + 1])
>			{
>				temp = arr[j];
>				arr[j] = arr[j + 1];
>				arr[j + 1] = temp;
>			}
>		}
>	}
>}
>
>void Display_arr(int *arr,int len)
>{
>	for (int i = 0; i < len; i++)
>	{
>		std::cout << arr[i] << " ";
>	}
>	std::cout << std::endl;
>}
>
>
>```
>
>

## 结构体

### 8.1结构体的基本概念

>结构体属于用户==自定义的数据类型==，允许用户存储不同的数据类型

### 8.2 结构体的定义和使用

>**语法：**`struct 结构体名 { 结构体成员列表 }；`
>
>通过结构体创建变量的方式有三种：
>
>* struct 结构体名 变量名
>* struct 结构体名 变量名 = { 成员1值 ， 成员2值...}
>* 定义结构体时顺便创建变量
>
>```c++
>//创建一个学生的数据类型
>#include<iostream>
>#include<string>
>
>
>//创建一个学生的数据类型
>//自定义数据类型，已有数据类型的一些集合
>struct Student    //此时的struct Student 跟int 一样，是一个数据类型
>{
>	std::string name;
>	int age;
>	int score;
>};
>//可以通过struct Student si;定义一个这个类型的变量
>
>int main()
>{
>	struct Student su1;//创建了一个该结构体变量,这里的struct可以省略
>	//通过 . 来访问结构体的属性
>	su1.name = "张三";  //给结构体变量内的属性赋值
>	su1.age = 20;
>	su1.score = 90;
>	std::cout << "姓名：" << su1.name << " 年纪：" << su1.age << " 分数：" << su1.score << std::endl;
>	//定义方式2
>	struct Student su2 = { "李四",21,80 };
>	std::cout << "姓名：" << su2.name << " 年纪：" << su2.age << " 分数：" << su2.score << std::endl;
>	system("pause");
>	return 0;
>}
>
>
>```
>
>>+ 定义结构体时的关键词struct，不可省略
>>+ 创建结构体变量时，关键词struct可以省略
>>+ 结构体变量利用操作符" . "访问成员。 

### 8.3结构体数组

>**作用：**将自定义的结构体放入到数组中方便维护
>
>**语法：**` struct  结构体名 数组名[元素个数] = {  {} , {} , ... {} }`
>
>```c++
>#include<iostream>
>#include<string>
>
>
>//创建一个学生的数据类型
>//自定义数据类型，已有数据类型的一些集合
>struct Student    //此时的struct Student 跟int 一样，是一个数据类型
>{
>	std::string name;
>	int age;
>	int score;
>};
>//可以通过struct Student si;定义一个这个类型的变量
>
>int main()
>{
>	struct Student arr[] =
>	{
>		{"ttt",20,100},
>		{"张三",18,80 },
>		{"李四",19,60 },
>		{"王五",20,70 }
>	};
>	for (int i = 0; i < 4; i++)
>	{
>		std::cout << "姓名：" << arr[i].name << " 年龄：" << arr[i].age << " 分数：" << arr[i].score << std::endl;
>	}
>	system("pause");
>	return 0;
>}
>
>
>```
>
>

### 8.4结构体指针

>**作用：**通过指针访问结构体中的成员
>
>
>
>* 利用操作符 `-> `可以通过结构体指针访问结构体属性
>
>```c++
>#include<iostream>
>#include<string>
>
>
>//创建一个学生的数据类型
>//自定义数据类型，已有数据类型的一些集合
>struct student    //此时的struct Student 跟int 一样，是一个数据类型
>{
>	std::string name;
>	int age;
>	int score;
>};
>//可以通过struct Student si;定义一个这个类型的变量
>
>int main()
>{
>	struct student s = { "张三",18,100 };
>	struct student* p = &s;
>	//通过指针来访问结构体
>	std::cout << "姓名："<<p->name<<" 年纪:"<< p->age<<" 成绩："<<p->score<<std::endl;
>	system("pause");
>	return 0;
>}
>
>```
>
>

### 8.5结构体嵌套结构体

>**作用：** 结构体中的成员可以是另一个结构体
>
>**例如：**每个老师辅导一个学员，一个老师的结构体中，记录一个学生的结构体
>
>```c++
>#include<iostream>
>#include<string>
>
>
>//创建一个学生的数据类型
>//自定义数据类型，已有数据类型的一些集合
>struct student    //此时的struct Student 跟int 一样，是一个数据类型
>{
>	std::string name;
>	int age;
>	int score;
>};
>//可以通过struct Student si;定义一个这个类型的变量
>
>struct teacher
>{
>	int id;
>	std::string name;
>	int age;
>	struct student stu1;//子结构体
>};
>
>int main()
>{
>	teacher t;
>	t.id = 10000;
>	t.name = "老王";
>	t.age = 40;
>	t.stu1.age = 20;
>	t.stu1.name = "李华";
>	t.stu1.score = 70;
>	std::cout << "老师的姓名：" << t.name << " 老师的编号：" << t.id << " 老师的年纪：" << t.age << "辅导的学生姓名 ："
>		<< t.stu1.name << "年纪" << t.stu1.age << "分数" << t.stu1.score << std::endl;
>	system("pause");
>	return 0;
>}
>
>
>```
>
>>**总结：**在结构体中可以定义另一个结构体作为成员，用来解决实际问题

### 8.6 结构体做函数参数

>**作用：**将结构体作为参数向函数中传递
>
>传递方式有两种 ：
>
>+ 值传递
>+ 地址传递
>
>```c++
>#include<iostream>
>#include<string>
>
>void PrintStudent(struct student);
>void PrintStudent2(struct student*);
>
>//创建一个学生的结构体类型
>struct student    //此时的struct Student 跟int 一样，是一个数据类型
>{
>	std::string name;
>	int age;
>	int score;
>};
>
>
>int main()
>{
>	student stu;
>	stu.name = "张三";
>	stu.age = 20;
>	stu.score = 100;
>	PrintStudent(stu);
>	PrintStudent2(&stu);
>	std::cout << "main函数中的姓名：" << stu.name 
>		      << " main函数中的年纪：" << stu.age 
>		      << " main函数中的分数：" << stu.score << std::endl;
>	system("pause");
>	return 0;
>}
>
>//值传递,子函数中修改值不会影响原函数的值
>void PrintStudent(struct student s)
>{
>	s.age = 25;
>	std::cout << "子函数中的姓名：" << s.name 
>			  << " 子函数中的年纪：" << s.age 
>		      << " 子函数中的分数：" << s.score << std::endl;
>}
>//地址传递，子函数中修改值，会影响原函数的值
>void PrintStudent2(struct student* s)
>{
>	s->age = 30;
>	std::cout << "子函数中的姓名：" << s->name 
>		      << " 子函数中的年纪：" << s->age 
>		      << " 子函数中的分数：" << s->score << std::endl;
>}
>```
>
>

### 结构体中const使用场景

>**作用：**用const来防止误操作
>
>```c++
>```
>
>
