# 基础1 数据类型、运算符、循环

# 1 变量
 - 变量存在的意义：**方便管理内存空间**
 - 语法：数据类型 变量名 = 变量初始值  int a  = 10

```cpp
#include<iostream>
using namespace std;

//变量存在的意义：方便管理内存空间
//语法：数据类型 变量名 = 变量初始值
int main()
{
	int a = 10;
	cout << "a = " << a << endl;
	system("pause");
	return 0;
}
```
# 2 常量(#define/const)
1. **\#define**  宏常量： `#define 常量名 常量值`
   * 通常在文件上方定义，表示一个常量

2. **const**  修饰的变量 `const 数据类型 常量名 = 常量值`
   * 通常在变量定义前加关键字const，修饰该变量为常量，不可修改

```cpp
#include<iostream>
using namespace std;

// 常量定义方式
// 1、 #define 宏常量 
// 2、 const 修饰的变量

// 1、#define 宏常量
#define Day 7

int main()
{
	//Day = 14;// 报错，Day是常量，一旦修改就报错
	cout << "一周总共有：" << Day << " 天" << endl;

	//2、const 修饰的变量
	const int month = 12;
	// month = 24;//报错，const修饰的变量成为常量
	cout << "一年总共有：" << month << " 月" << endl;

	system("pause");
	return 0;
}
```
# 3 标识符命名
**标识符命名规则**

 1.  不可以是关键字

 2. 由首字母、数字、下划线构成

 3. 第一个字符只能是字母或者下划线

 4. 标识符区分大小写

建议：**给变量取名的时候，最好能够做到见名知意**

# 4 数据类型
## 4.1 整型
![在这里插入图片描述](https://img-blog.csdnimg.cn/2aee9480c2b849dbb0e8780747967e32.png)	
|    **数据类型**     |                  **占用空间**                   |     取值范围     |
| :-----------------: | :---------------------------------------------: | :--------------: |
|    short(短整型)    |                      2字节                      | (-2^15 ~ 2^15-1) |
|      int(整型)      |                      4字节                      | (-2^31 ~ 2^31-1) |
|    long(长整形)     | Windows为4字节，Linux为4字节(32位)，8字节(64位) | (-2^31 ~ 2^31-1) |
| long long(长长整形) |                      8字节                      | (-2^63 ~ 2^63-1) |

## 4.2 sizeof关键字
 - **利用 sizeof 求出数据类型占用内存大小**
 - 语法：sizeof(数据类型/变量)
 - 整型：short(2)  int(4)  long(4)  long long (8)

```cpp
#include<iostream>
using namespace std;

int main()
{
	//整型：short(2)  int(4)  long(4)  long long (8)
	//利用sizeof求出数据类型占用内存大小
	//语法：sizeof(数据类型 / 变量)

	short num1 = 10;
	cout << "num1 占用的内存空间: " << sizeof(num1) << endl;
	cout << "short 占用的内存空间: " << sizeof(short) << endl;
	//写成sizeof(short)也可以

	int num2 = 10;
	cout << "int 占用的内存空间: " << sizeof(int) << endl;

	long num3 = 10;
	cout << "long 占用的内存空间: " << sizeof(long) << endl;

	long long num4 = 10;
	cout << "long long 占用的内存空间: " << sizeof(long long) << endl;

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/d66e63fd376240058c65c3d08adb0ead.png)	
## 4.3 实型(浮点型)
浮点型变量分为两种：

1. 单精度 float 4字节
2. 双精度 double 8字节
3. 默认情况下 输出一个小数，会显示出6位有效数字

| **数据类型** | **占用空间** | **有效数字范围** |
| ------------ | ------------ | ---------------- |
| float        | 4字节        | 7位有效数字      |
| double       | 8字节        | 15～16位有效数字 |

```cpp
int main() {

	float f1 = 3.14f;
	double d1 = 3.14;

	cout << f1 << endl;
	cout << d1<< endl;

	cout << "float  sizeof = " << sizeof(f1) << endl;4个字节
	cout << "double sizeof = " << sizeof(d1) << endl;8个字节

	//科学计数法
	float f2 = 3e2; // 3 * 10 ^ 2 
	cout << "f2 = " << f2 << endl;

	float f3 = 3e-2;  // 3 * 0.1 ^ 2
	cout << "f3 = " << f3 << endl;

	system("pause");
	return 0;
}
```
## 4.4 字符型(单个字符)
**大小为1个字节**
字符型变量用于显示单个字符：char ch = 'a';`

> 注意1：在显示字符型变量时，用**单引号将字符括起来**，不要用双引号
> 注意2：**单引号内只能有一个字符**，不可以是字符串

- **C和C++中字符型变量只占用1个字节**
- 字符型变量不是把字符本身放到内存中存储，而是**将对应的ASCII编码放入到存储单元**
- a —— 97	A —— 65

```cpp
#include<iostream>
using namespace std;

int main() {

	//1、字符型变量创建方式
	char ch = 'a';
	cout << ch << endl;

	//2、字符型变量所占内存大小
	cout << sizeof(char) << endl;

	//3、字符型变量常见错误
	//ch = "abcde"; //错误，不可以用双引号，创建字符型变量时，要用单引号
	//ch = 'abcde'; //错误，单引号内只能引用一个字符

	//4、字符型变量对应的ASCII编码
	// a —— 97	A —— 65
	cout << (int)ch << endl;  //查看字符a对应的ASCII码，97
	ch = 97; //可以直接用ASCII给字符型变量赋值
	cout << ch << endl; // a

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/b1ebecb7884c4a68a5cda9a9b219444b.png)	
## 4.5 转义字符
| **转义字符** |                **含义**                 | **ASCII**码值(十进制) |
| :----------: | :-------------------------------------: | :-------------------: |
|      \a      |                  警报                   |          007          |
|      \b      |     退格(BS) ，将当前位置移到前一列     |          008          |
|      \f      |    换页(FF)，将当前位置移到下页开头     |          012          |
|    **\n**    | **换行(LF) ，将当前位置移到下一行开头** |        **010**        |
|      \r      |    回车(CR) ，将当前位置移到本行开头    |          013          |
|    **\t**    | **水平制表(HT)  （跳到下一个TAB位置）** |        **009**        |
|      \v      |              垂直制表(VT)               |          011          |
|   **\\\\**   |        **代表一个反斜线字符"\"**        |        **092**        |
|      \'      |       代表一个单引号（撇号）字符        |          039          |
|      \"      |           代表一个双引号字符            |          034          |
|      \?      |              代表一个问号               |          063          |
|      \0      |                  数字0                  |          000          |
|     \ddd     |         8进制转义字符，d范围0~7         |       3位8进制        |
|     \xhh     |   16进制转义字符，h范围0~9，a~f，A~F    |       3位16进制       |

 - **换行符  \n：起到换行的作用**
 - **反斜杠 \\ ：两个反斜杠输出一个反斜杠**
 - **水平制表符 \t ：整齐输出数据，数值和\t加起来有8个空格**

```cpp
#include<iostream>
using namespace std;

// 转义字符
int main()
{
	// 1.换行符 \n
	cout << "hello world\n";

	// 2.反斜杠 \\
	cout << "\\" << endl;//两个反斜杠输出一个反斜杠

	// 水平制表符 \t 整齐输出数据
	cout << "aaa\thelloworld" << endl;
	cout << "a\thelloworld" << endl;
	cout << "aaaaa\thelloworld" << endl;
	system("pause");
	return 0;
}
```
- 结果

![在这里插入图片描述](https://img-blog.csdnimg.cn/02bda087eadb48f89246944e1a76bb1b.png)	

## 4.6 字符串型(两种风格)
 - **C风格字符串**： `char 变量名[] = "字符串值"`
 - C风格的字符串要**用双引号括起来**

```cpp
char str[] = "hello world";
cout << str << endl;
```
 - **C++风格字符串**：  `string  变量名 = "字符串值"`
 - C++风格字符串，需要加入头文件**#include\<string>**

```cpp
string str2 = "hello world";
cout << str2 << endl;
```

```cpp
#include<iostream>
#include<string>//C++风格的字符串要包含头文件
using namespace std;

int main()
{
	// 1.C风格字符串
	// 注意：char字符串名[];等号后用双引号包含字符串;
	// 注意事项1  char 字符串名[]
	// 注意事项2 等号后面 要用双引号 包含起来字符串
	char str[] = "hello world";
	cout << str << endl;

	// 2.C++风格字符串
	// 包含头文件#include<string>
	string str2 = "hello world";
	cout << str2 << endl;

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/405dd38d7efc487dbe44220c0458cc98.png)	
## 4.7 bool类型
 - **bool类型占1个字节大小**

```cpp
#include<iostream>
using namespace std;

int main()
{
	// 1.创建bool数据类型
	bool flag = true;// true 代表真
	cout << flag << endl; // 1

	flag = false;// false 代表假
	cout << flag << endl; // 0

	// 本质上 1代表真，0代表假

	// 2.查看bool类型所占内存空间
	cout << "size of bool = " << sizeof(bool) << endl; // 1

	system("pause");
	return 0;
}
```
## 4.8 数据输入
 - 从键盘获取数据：**cin >> 变量**

```cpp
#include<iostream>
#include<string> // C++ string头文件
using namespace std;

int main()
{
	// 1.整型输入
	int a = 0;
	cout << "请输入整型变量：" << endl;
	cin >> a;
	cout << "整型变量a = " << a << endl;

	// 2.浮点型输入
	float f = 3.14f;
	cout << "请输入浮点型变量：" << endl;
	cin >> f;
	cout << "浮点型变量f = " << f << endl;

	// 3.字符型输入
	char ch = 0;
	cout << "请输入字符型变量：" << endl;
	cin >> ch;
	cout << "字符型变量ch = " << ch << endl;

	// 4.字符串型输入
	string str;
	cout << "请输入字符串型变量：" << endl;
	cin >> str;
	cout << "字符串变量str = " << str << endl;

	// 5.布尔类型输入
	bool flag = true;
	cout << "请输入布尔型变量：" << endl;
	cin >> flag;// bool类型，只要是非0的值都代表了真
	cout << "布尔型变量flag = " << flag << endl;

	system("pause");
	return 0;
}
```
# 5 运算符
| **运算符类型** | **作用**                               |
| -------------- | -------------------------------------- |
| 算术运算符     | 用于处理四则运算                       |
| 赋值运算符     | 用于将表达式的值赋给变量               |
| 比较运算符     | 用于表达式的比较，并返回一个真值或假值 |
| 逻辑运算符     | 用于根据表达式的值返回真值或假值       |

## 5.1 算术运算符
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
### 5.1.1 加减乘除
 - 在除法运算中，除数不能为0

```cpp
//加减乘除
int main() {

	int a1 = 10;
	int b1 = 3;

	cout << a1 + b1 << endl;
	cout << a1 - b1 << endl;
	cout << a1 * b1 << endl;
	cout << a1 / b1 << endl;  // 两个整数相除结果依然是整数

	int a2 = 10;
	int b2 = 20;
	cout << a2 / b2 << endl; 

	int a3 = 10;
	int b3 = 0;
	//cout << a3 / b3 << endl; //报错，除数不可以为0

	//两个小数可以相除
	double d1 = 0.5;
	double d2 = 0.25;
	cout << d1 / d2 << endl;

	system("pause");
	return 0;
}
```
### 5.1.2 取模
![在这里插入图片描述](https://img-blog.csdnimg.cn/9eeb0ffa1f0649b39a22547fa3871404.png)
 - **只有整数有取模运算**
 - 取模运算本质就是求**余数**

```cpp
//取模
int main() {

	int a1 = 10;
	int b1 = 3;

	cout << 10 % 3 << endl;

	int a2 = 10;
	int b2 = 20;

	cout << a2 % b2 << endl;

	int a3 = 10;
	int b3 = 0;

	//cout << a3 % b3 << endl; //取模运算时，除数也不能为0

	//两个小数不可以取模
	double d1 = 3.14;
	double d2 = 1.1;

	//cout << d1 % d2 << endl;

	system("pause");
	return 0;
}
```
### 5.1.3 自加自减
 - 前置递增先对变量进行++，再计算表达式，后置递增相反

```cpp
#include<iostream>
using namespace std;

int main()
{
	// 后置递增
	int a = 10;
	a++; // 等价于a = a + 1
	cout << a << endl; // 11

	// 前置递增
	int b = 10;
	++b;
	cout << b << endl; // 11

	// 区别
	// 前置递增：先对变量进行++，再计算表达式
	int a2 = 10;
	int b2 = ++a2 * 10;
	cout << "a2 = " << a2 << endl;// 11
	cout << "b2 = " << b2 << endl;// 110

	// 后置递增：先计算表达式，后对变量进行++
	int a3 = 10;
	int b3 = a3++ * 10;
	cout << "a3 = " << a3 << endl;// 11
	cout << "b3 = " << b3 << endl;// 100

	system("pause");
	return 0;
}
```
## 5.2 赋值运算符
| **运算符** | **术语** | **示例**   | **结果**  |
| ---------- | -------- | ---------- | --------- |
| =          | 赋值     | a=2; b=3;  | a=2; b=3; |
| +=         | 加等于   | a=0; a+=2; | a=2;      |
| -=         | 减等于   | a=5; a-=3; | a=2;      |
| *=         | 乘等于   | a=2; a*=2; | a=4;      |
| /=         | 除等于   | a=4; a/=2; | a=2;      |
| %=         | 模等于   | a=3; a%2;  | a=1;      |

```cpp
int main() {

	// 赋值运算符

	// =
	int a = 10;
	a = 100;
	cout << "a = " << a << endl;

	// +=
	a = 10;
	a += 2; // a = a + 2;
	cout << "a = " << a << endl;

	// -=
	a = 10;
	a -= 2; // a = a - 2
	cout << "a = " << a << endl;

	// *=
	a = 10;
	a *= 2; // a = a * 2
	cout << "a = " << a << endl;

	// /=
	a = 10;
	a /= 2;  // a = a / 2;
	cout << "a = " << a << endl;

	// %=
	a = 10;
	a %= 2;  // a = a % 2;
	cout << "a = " << a << endl;

	system("pause");
	return 0;
}
```
## 5.3 比较运算符
 - 用于表达式的比较，并返回一个真值或假值

| **运算符** | **术语** | **示例** | **结果** |
| ---------- | -------- | -------- | -------- |
| ==         | 相等于   | 4 == 3   | 0        |
| !=         | 不等于   | 4 != 3   | 1        |
| <          | 小于     | 4 < 3    | 0        |
| \>         | 大于     | 4 > 3    | 1        |
| <=         | 小于等于 | 4 <= 3   | 0        |
| \>=        | 大于等于 | 4 >= 1   | 1        |

```cpp
#include<iostream>
using namespace std;

int main()
{
	int a = 10;
	int b = 20;
	// ==
	cout << (a == b) << endl; // 0 
	// !=
	cout << (a != b) << endl; // 1
	// >
	cout << (a > b) << endl; // 0
	// <
	cout << (a < b) << endl; // 1
	// >=
	cout << (a >= b) << endl; // 0
	// <=
	cout << (a <= b) << endl; // 1

	system("pause");
	return 0;
}
```
## 5.4 逻辑运算符
| **运算符** | **术语** | **示例** | **结果**                                               |
| ---------- | -------- | -------- | ------------------------------------------------------ |
| !          | 非       | !a       | 如果a为假，则!a为真；  如果a为真，则!a为假             |
| &&         | 与       | a && b   | 如果a和b都为真，则结果为真，否则为假                   |
| \|\|       | 或       | a \|\| b | 如果a和b有一个为真，则结果为真，二者都为假时，结果为假 |

 - 逻辑 —— **非**
```cpp
//逻辑运算符  --- 非
int main() {

	int a = 10;

	cout << !a << endl; // 0
	cout << !!a << endl; // 1

	system("pause");
	return 0;
}
```

 - 逻辑 —— **与**
![在这里插入图片描述](https://img-blog.csdnimg.cn/d0ca8a4b927949eca7694456dcf05e7e.png)
```cpp
//逻辑运算符  --- 与
int main() {

	int a = 10;
	int b = 10;

	cout << (a && b) << endl;// 1

	a = 10;
	b = 0;

	cout << (a && b) << endl;// 0 

	a = 0;
	b = 0;

	cout << (a && b) << endl;// 0

	system("pause");
	return 0;
}
```
 - 逻辑 —— **或**
![在这里插入图片描述](https://img-blog.csdnimg.cn/e1a570b136d844389452ba2d4195765f.png)
```cpp
//逻辑运算符  --- 或
int main() {

	int a = 10;
	int b = 10;

	cout << (a || b) << endl;// 1

	a = 10;
	b = 0;

	cout << (a || b) << endl;// 1 

	a = 0;
	b = 0;

	cout << (a || b) << endl;// 0

	system("pause");
	return 0;
}
```
# 6 程序结构
## 6.1 选择结构
 - 依据条件是否满足，有选择的执行相应功能

### 6.1.1 多行if语句
```cpp
#include<iostream>
using namespace std;

int main()
{
	int score = 0;

	cout << "请输入考试分数：" << endl;
	cin >> score;

	if (score > 600)
	{
		cout << "我考上了一本大学" << endl;
	}
	else
	{
		cout << "我未考上一本大学" << endl;
	}

	system("pause");
	return 0;
}
```
### 6.1.2 嵌套if语句
```cpp
#include<iostream>
using namespace std;

int main()
{
	//提示用户输入一个高考考试分数，根据分数做如下判断
	//如果大于600分视为考上一本，大于500分考上二本，大于400考上三本，其余视为未考上本科；
	//在一本分数中，如果大于700分，考入北大，大于650分，考入清华，大于600考入人大。
	int score = 0;
	cout << "请输入高考分数：" << endl;
	cin >> score;
	cout << "输入的分数为：" << score << endl;
	if (score > 600)
	{
		cout << "考入一本" << endl;
		if (score > 700)
		{
			cout << "考入北大" << endl;
		}
		else if (score > 650)
		{
			cout << "考入清华" << endl;
		}
		else
		{
			cout << "考入人大" << endl;
		}
	}
	else if (score > 500)
	{
		cout << "考入二本" << endl;
	}
	else if (score > 400)
	{
		cout << "考入三本" << endl;
	}
	else
	{
		cout << "未考上" << endl;
	}
	system("pause");
	return 0;
}
```
### 6.1.3 练习 — 三只小猪称重
> 有三只小猪ABC，请分别输入三只小猪的体重，并且判断哪只小猪最重？

![在这里插入图片描述](https://img-blog.csdnimg.cn/b4c50f83429a495b925d219616f6f68f.png)

```cpp
#include<iostream>
using namespace std;

int main()
{
	//有三只小猪ABC，请分别输入三只小猪的体重，并且判断哪只小猪最重

	//1.创建3只小猪的体重变量
	int num1 = 0;
	int num2 = 0;
	int num3 = 0;

	//2.让用户输入三只小猪的重量
	cout << "请输入小猪A的体重" << endl;
	cin >> num1;

	cout << "请输入小猪B的体重" << endl;
	cin >> num2;

	cout << "请输入小猪C的体重" << endl;
	cin >> num3;

	cout << "小猪A的体重为：" << num1 << endl;
	cout << "小猪B的体重为：" << num2 << endl;
	cout << "小猪C的体重为：" << num3 << endl;

	//3.判断哪只最重
	//先判断A和B的重量
	if (num1 > num2)	//A比B重
	{
		if (num1 > num3)	//A比C重
		{
			cout << "小猪A最重" << endl;
		}
		else     //C比A重
		{
			cout << "小猪C最重" << endl;
		}
	}
	else   //B比A重
	{
		if (num2 > num3)	//B比C重
		{
			cout << "小猪B最重" << endl;
		}
		else     //C比B重
		{
			cout << "小猪C最重" << endl;
		}
	}

	system("pause");
	return 0;
}
```
### 6.1.4 三目运算
> 表达式1 ? 表达式2 ：表达式3
> 如果表达式1的值为真，执行表达式2，并返回表达式2的结果；
> 如果表达式1的值为假，执行表达式3，并返回表达式3的结果。

```cpp
#include<iostream>
using namespace std;

int main()
{
	//创建a,b,c,将变量大的值赋值给变量c
	//将a和b作比较，将变量大的值赋值给变量c

	int a = 10;
	int b = 20;
	int c = 0;

	c = a > b ? a : b;

	cout << "c = " << c << endl;// c = b 为20

	//C++中三目运算符返回的是变量,可以继续赋值
	(a > b ? a : b) = 100;

	cout << "a = " << a << endl;// 10
	cout << "b = " << b << endl;// 100
	cout << "c = " << c << endl;// 20

	cout << "hello world" << endl;

	system("pause");
	return 0;
}
```
### 6.1.5 switch语句
- 表达式

```bash
switch(表达式)

{
	case 结果1：执行语句;break;
	case 结果2：执行语句;break;
	...
	default:执行语句;break;
}
```
**if和switch的区别**

 - switch的缺点：判断时候只能是**整型或者字符型**，不可以是一个区间
 - switch的优点：结构清晰，执行效率高

```cpp
#include<iostream>
using namespace std;

int main()
{
	//请给电影评分 
	//10 ~ 9   经典   
	// 8 ~ 7   非常好
	// 6 ~ 5   一般
	// 5分以下 烂片

	//1.提示用户给电影打分
	cout << "请给电影打分" << endl;
	//2.用户开始进行打分
	int score = 0;
	cin >> score;
	cout << "您打的分数为：" << score << endl;
	//3.根据用户输入的分数提示用户最后的结果
	switch (score)
	{
	case 10:
	case 9:
		cout << "经典" << endl;
		break;// 退出当前分支
	case 8:
		cout << "非常好" << endl;
		break;
	case 7:
	case 6:
		cout << "一般" << endl;
		break;
	default://以上这些选择都没有选到
		cout << "烂片" << endl;
		break;
	}
	system("pause");
	return 0;
}
```
## 6.2 循环结构
### 6.2.1 while循环
```cpp
#include<iostream>
using namespace std;

int main()
{
	// while循环
	// 屏幕中打印0~9打印
	int num = 0;
	while (num < 10)
	{
		cout << "num = " << num << endl;
		num++;
	}
	system("pause");
	return 0;
}
```
### 6.2.2 while循环练习：猜数字
![在这里插入图片描述](https://img-blog.csdnimg.cn/f83377e0eb3247b4b0f2188cb98a5052.png)
#### 6.2.2.1 添加随机数种子(#include\<ctime>)
```cpp
// time系统时间文件的包含
#include<ctime>
// 添加随机数种子，作用：利用当前系统时间生成随机数，防止每次随机数都一样
srand((unsigned int)time(NULL));
// 1.系统生成随机数,rand()%100——生成0~99的随机数
int num = rand() % 100 + 1; //rand()%100+1 生成 1~100 的随机数
```
#### 6.2.2.2 while猜测
```cpp
#include<iostream>
using namespace std;
// time系统时间文件的包含
#include<ctime>

int main()
{
	// 添加随机数种子，作用：利用当前系统时间生成随机数，防止每次随机数都一样
	srand((unsigned int)time(NULL));

	// 1.系统生成随机数,rand()%100——生成0~99的随机数
	int num = rand() % 100 + 1; // rand()%100+1 生成 1~100 的随机数
	//cout << num << endl;

	// 2.玩家进行猜测
	int val = 0;	// 玩家输入的数据
	while (1)
	{
		cin >> val;

		// 3.判断玩家的猜测
		if (val > num)
		{
			cout << "猜测过大" << endl;
		}
		else if (val < num)
		{
			cout << "猜测过小" << endl;
		}
		else
		{
			cout << "猜对了" << endl;
			// 猜对 退出游戏
			break; // break可以利用当前关键字退出当前循环
		}
	}
	// 猜错 提示猜的结果 过大或者过小 重新返回第2步
	system("pause");
	return 0;
}
```
### 6.2.3 do while循环
 - 与while循环区别在于，do...while先执行一次循环语句，再判断循环条件

```cpp
#include<iostream>
using namespace std;

int main()
{
	// do while 语句
	int num = 0;

	do
	{
		cout << "num = " << num << endl;
		num++;
	} while (num < 10);
	// do while和while的区别是在于do while  会先执行一次循环

	system("pause");
	return 0;
}
```
###  6.2.4 do while循环练习：水仙花数

> 案例描述：水仙花数是指一个 3 位数，它的**每个位上的数字的 3次幂之和等于它本身**
> 例如：1^3 + 5^3+ 3^3 = 153
> 请利用do...while语句，求出所有3位数中的水仙花数

![在这里插入图片描述](https://img-blog.csdnimg.cn/871dacea48ad448f8104789d31fdd3fe.png)

```cpp
#include<iostream>
using namespace std;

int main()
{
	// 100~999获取每位数据
	// 获取个位：对数字取模于10 
	// 获取十位：先整除于10，得到两位数，再取模于10
	// 获取百位：直接整除100

	// 1.先打印所有的三位数
	int num = 100;

	do
	{
		// 2.从所有三位数中找到水仙花数
		int a = 0;
		int b = 0;
		int c = 0;

		a = num % 10;// 获取个位
		b = num / 10 % 10;// 获取十位
		c = num / 100;// 获取百位

		if (a * a * a + b * b * b + c * c * c == num)// 如果是水仙花数打印
		{
			cout << num << endl;
		}

		num++;
	} while (num < 1000);

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/4cc9232a6d0b456d840a5056bf68949e.png)	
### 6.2.5 for循环
 - for循环中的表达式，要用分号进行分隔

> for(起始表达式;条件表达式;末尾循环体) { 循环语句; }

```cpp
#include<iostream>
using namespace std;

int main()
{
	// for循环
	// 数字0打印到数字9
	int i = 0;
	for (; ;)
	{
		if (i >= 10)
		{
			break;
		}
		cout << i << endl;
		i++;
	}
	system("pause");
	return 0;
}
```

```cpp
#include<iostream>
using namespace std;

int main()
{
	// for循环
	// 数字0打印到数字9
	for (int i = 0; i < 10; i++)
	{
		cout << i << endl;
	}

	system("pause");
	return 0;
}
```

 - 详解

![在这里插入图片描述](https://img-blog.csdnimg.cn/5b5e31faed64472caa2601efc0a922dc.png)

### 6.2.6 for循环练习：敲桌子
> 案例描述：从1开始数到数字100， 如果数字个位含有7，或者数字十位含有7，或者该数字是7的倍数，我们打印敲桌子，其余数字直接打印输出。

 - 分析

![在这里插入图片描述](https://img-blog.csdnimg.cn/44be78e86ba446a18a1788bbff42d08f.png)
```cpp
#include<iostream>
using namespace std;

int main()
{
	// 敲桌子
	// 1、输出1~100数字
	for (int i = 1; i <= 100; i++)
	{
		// 2、从100个数字中找到特殊数字，打印“敲桌子”
		// 如果是7的倍数、个位有7、或者十位有7，打印敲桌子
		if (i % 7 == 0 || i % 10 == 7 || i / 10 == 7) // 如果是特殊数字，打印敲桌子
		{
			cout << "敲桌子" << endl;
		}
		else // 如果不是特殊数字，打印数字
		{
			cout << i << endl;
		}
	}
}
```
### 6.2.7 嵌套循环
 - 在循环体中再嵌套一层循环
 - 在屏幕中打印如下图片，就需要利用嵌套循环
![在这里插入图片描述](https://img-blog.csdnimg.cn/455aeaadf7c64afaa8f420a2a6e9e9dc.png)

```cpp
#include<iostream>
using namespace std;

int main()
{
	// 利用嵌套循环实现星图
	// 打印一行星图
	for (int i = 0; i < 10; i++)	// 做10次操作下面的操作
	{
		for (int j = 0; j < 10; j++)
		{
			cout << "* ";
		}
		cout << endl;// 做换行处理
	}

	system("pause");
	return 0;
}
```
### 6.2.8 嵌套循环练习：乘法口诀表
![在这里插入图片描述](https://img-blog.csdnimg.cn/89e7e33607124e20b5e1e71b652f0eba.png)
 - 分析
![](https://img-blog.csdnimg.cn/d449a1581d7e4a78831a868f581159aa.png)

```cpp
#include<iostream>
using namespace std;
//列数<=当前行数
int main()
{
	// 乘法口诀表	列数*行数=结果    列数<=当前行数
	// 打印行数
	for (int i = 1; i <= 9; i++)	// 行数
	{
		for (int j = 1; j <= i; j++)	// 列数
		{
			cout << j << " * " << i << " = " << j * i << "\t";
		}
		cout << endl;
	}
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/a53fb04ff15b4fafa3adc6c27c409e29.png)

## 6.3 跳转语句
### 6.3.1 break语句
break使用的时机：

 - 出现在switch条件语句中，作用是终止case并跳出switch
 - 出现在循环语句中，作用是跳出当前的循环语句
 - 出现在嵌套循环中，跳出最近的内层循环语句

```cpp
#include<iostream>
using namespace std;

int main()
{
	// 出现在switch条件语句中，作用是终止case并跳出switch
	// 出现在循环语句中，作用是跳出当前的循环语句
	// 出现在嵌套循环中，跳出最近的内层循环语句

	// 1.出现在switch中

	cout << "请选择副本难度" << endl;
	cout << "1.普通" << endl;
	cout << "2.中等" << endl;
	cout << "3.困难" << endl;

	int select = 0;		// 创建选择结果的变量

	cin >> select;	// 等待用户的输入

	switch (select)
	{
	case 1:
		cout << "您选择的是普通难度" << endl;
		break;
	case 2:
		cout << "您选择的是中等难度" << endl;
		break;
	case 3:
		cout << "您选择的是困难难度" << endl;
		break;
	default:	// 默认情况下输入
		break;
	}

	// 2.出现在循环语句
	for (int i = 0; i < 10; i++)
	{
		// 如果i等于5，退出循环，不再打印
		if (i == 5)
		{
			break;	// 退出循环
		}
		cout << i << endl;
	}

	// 3.出现在嵌套循环语句中
	for (int i = 0; i < 10; i++)	// 做10次操作下面的操作
	{
		for (int j = 0; j < 10; j++)
		{
			if (j == 5)
			{
				break;	// 退出内层循环，即影响j
			}
			cout << "* ";
		}
		cout << endl;// 做换行处理
	}

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/dadc3ba0a5984ed0ba690066ad70c998.png)	

### 6.3.2 continue语句
![在这里插入图片描述](https://img-blog.csdnimg.cn/20b7c5a958c74af09f59557436c0f913.png)
 - 在==循环语句==中，跳过本次循环中余下尚未执行的语句，继续执行下一次循环

```cpp
#include<iostream>
using namespace std;

// continue:执行到本行，就不再执行后面的代码，而执行下一次循环
int main()
{
	// continue语句
	for (int i = 0; i <= 100; i++)
	{
		// 奇数输出，偶数不输出
		if (i % 2 == 0)
		{
			continue;	// 筛选条件，执行到此就不再向下执行，执行下一次循环
			// break会退出循环，continue不会
		}
		cout << i << endl;
	}
	system("pause");
	return 0;
}
```

# 基础2 数组、函数

# 7 一维数组

## 7.1 一维数组定义
![在这里插入图片描述](https://img-blog.csdnimg.cn/f0a72d1dbd324f58be5aea7610d51047.png)
一维数组定义的三种方式：

1. ` 数据类型  数组名[ 数组长度 ]; `
2. `数据类型  数组名[ 数组长度 ] = { 值1，值2 ...};`
3. `数据类型  数组名[ ] = { 值1，值2 ...};`

```cpp
#include<iostream>
using namespace std;

int main()
{
	// 定义方式1
	// 数据类型 数组名[元素个数];
	int score[10];

	// 利用下标赋值,从0开始索引
	score[0] = 100;
	score[1] = 99;
	score[2] = 85;

	// 利用下标输出
	cout << score[0] << endl;
	cout << score[1] << endl;
	cout << score[2] << endl;

	// 第二种定义方式
	// 数据类型 数组名[元素个数] =  {值1，值2 ，值3 ...};
	// 如果{}内不足10个数据，剩余数据用0补全
	int score2[10] = { 100,90,80,70,60,50,40,30,20,10 };

	// 逐个输出
	// cout << score2[0] << endl;
	// cout << score2[1] << endl;

	// 一个一个输出太麻烦，因此可以利用循环进行输出
	for (int i = 0; i < 10; i++)
	{
		cout << score2[i] << endl;
	}

	// 定义方式3
	// 数据类型 数组名[] =  {值1，值2 ，值3 ...};
	int score3[] = { 100,90,80,70,60,50,40,30,20,10 };
	for (int i = 0; i < 10; i++)
	{
		cout << score3[i] << endl;
	}

	system("pause");
	return 0;
}
```
## 7.2 一维数组数组名(重点)
![在这里插入图片描述](https://img-blog.csdnimg.cn/4746f46130bb4c5883518cf4978fac84.png)

一维数组名称的**用途**：

 - **统计整个数组在内存中的长度**：sizeof(arr)
 - **获取数组在内存中的首地址，这里的地址指的是字节的地址**：`arr数组名就是数组的首地址`

程序如下

 - **可获取整个数组占用的空间，sizeof(arr)，整型是4个字节大小**

```cpp
int arr[10] = { 1,2,3,4,5,6,7,8,9,10 };
cout << "整个数组占用内存空间大小为： " << sizeof(arr) << endl;
cout << "每个数组占用内存空间大小为： " << sizeof(arr[0]) << endl;
cout << "数组元素个数为： " << sizeof(arr) / sizeof(arr[0]) << endl;
```
 - 结果
![在这里插入图片描述](https://img-blog.csdnimg.cn/051a259ae8714fffa5559db13dee35ac.png)
 - **可通过数组名称查看数组在内存中的首地址,cout << arr << endl**
 - `数组名就是数组的首地址`

```cpp
cout << "数组首地址为：" << (int)arr << endl;// 10进制地址
cout << "数组首地址为：" << arr << endl;// 16进制地址
cout << "数组第一个元素地址为：" << (int)&arr[0] << endl;
cout << "数组第二个元素地址为：" << (int)&arr[1] << endl;//整型是四个字节
```
 - 结果
 ![](https://img-blog.csdnimg.cn/860e2f92d4a14989abcfdc3b03b6b7d3.png)
 - 总结如下
 - 注意：数组名是常量，不可以赋值
 - 总结1：直接打印数组名，可以查看**数组所占内存的首地址**
 - 总结2：对数组名进行sizeof，可以获取**整个数组占内存空间的大小**

## 7.3 一维数组练习1：五只小猪称体重
**案例描述**：在一个数组中记录了五只小猪的体重，如：int arr[5] = {300,350,200,400,250}；找出并打印最重的小猪体重。

 - 分析
![在这里插入图片描述](https://img-blog.csdnimg.cn/bf31312b81f14c5d893589ed0617032f.png)
```cpp
#include<iostream>
using namespace std;

int main()
{
	// 1.创建5只小猪的体重
	int arr[5] = { 300,350,200,400,250 };

	// 2.从数组中找最大值
	int max = 0;

	// 访问数组中的每个元素，如果这个元素比我认定的最大值大，更新最大值
	for (int i = 0; i < 5; i++)
	{
		if (arr[i] > max)
		{
			max = arr[i];
		}
	}

	// 3.打印最大值
	cout << "最重的小猪体重：" << max;
}
```
## 7.4 一维数组练习2：数组元素逆置
**案例描述**：请声明一个5个元素的数组，并且将元素逆置(如原数组元素为：1,3,2,5,4;逆置后输出结果为:4,5,2,3,1)。
- 分析
![在这里插入图片描述](https://img-blog.csdnimg.cn/8ffed8e7bc73434aa1990fad9e7e3448.png)

```cpp
#include<iostream>
using namespace std;

int main()
{
	// 请声明一个5个元素的数组，并且将元素逆置
	// 如原数组元素为：1, 3, 2, 5, 4; 逆置后输出结果为:4, 5, 2, 3, 1

	// 1.创建数组
	int arr[5] = { 1,3,2,5,4 };
	cout << "数组元素逆置前：" << endl;
	for (int i = 0; i < 5; i++)
	{
		cout << arr[i] << endl;
	}

	// 2.实现逆置
	// 2.1记录起始下标的位置
	// 2.2记录结束下标的位置
	// 2.3起始下标与结束下标的元素互换
	// 2.4起始位置++ 结束位置--
	// 2.5循环执行2.1的操作，直到起始位置>=结束位置
	int start = 0;// 2.1 起始下标
	int end = sizeof(arr) / sizeof(arr[0]) - 1;// 2.2 结束下标

	while (start < end)// 2.5 循环条件
	{
		// 2.3 元素互换
		int temp = arr[0];
		arr[start] = arr[end];
		arr[end] = temp;

		// 2.4 下标更新
		start++;
		end--;
	}

	// 3.打印逆置后的数组
	cout << "数组元素逆置后：" << endl;
	for (int i = 0; i < 5; i++)
	{
		cout << arr[i] << endl;
	}

	system("pause");
	return 0;
}
```
## 7.5 冒泡排序
**作用：** 最常用的排序算法，对数组内元素进行排序

 - 比较相邻的元素。如果第一个比第二个大，就交换他们两个。
 - 对每一对相邻元素做同样的工作，执行完毕后，找到第一个最大值。
 - 重复以上的步骤，每次比较次数-1，直到不需要比较

**示例：** 将数组 { 4,2,8,0,5,7,1,3,9 } 进行升序排序
![在这里插入图片描述](https://img-blog.csdnimg.cn/6bf4dfbdd53548fca6264fe8f3eb56e9.png)
 - **分析**
 - **排序总轮数 = 元素个数 - 1（i的范围）**
 - **每轮对比次数 = 元素个数 - 排序轮数 - 1（j的范围）**
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/9203109a3cd54f988a041cef471810b7.png)

```cpp
#include<iostream>
using namespace std;

int main()
{
	//1.比较相邻的元素。如果第一个比第二个大，就交换他们两个。
	//2.对每一对相邻元素做同样的工作，执行完毕后，找到第一个最大值。
	//3.重复以上的步骤，每次比较次数 - 1，直到不需要比较
	//9个元素第一轮做8次交换，找到第1个最大数，第二轮做7次交换，找到第2个最大数

	//1.利用冒泡排序实现升序排列
	int arr[9] = { 4,2,8,0,5,7,1,3,9 };
	cout << "排序前：" << endl;
	for (int i = 0; i < 9; i++)
	{
		cout << arr[i] << " ";
	}
	cout << endl;

	//2.冒泡排序 
	//排序的总轮数 = 元素个数 - 1
	int temp;
	for (int i = 0; i < 9 - 1; i++) //外侧排序的轮数
	{
		//内层的循环对比 每轮对比的次数 = 元素个数 - 排序轮数(第几轮，从0开始算起) - 1
		for (int j = 0; j < 9 - i - 1; j++)
		{
			//如果第一个数字，比第二个数字大，就交换这两个数字
			if (arr[j] > arr[j + 1])
			{
				// int temp = arr[j];// temp 要进行赋值
				temp = arr[j];
				arr[j] = arr[j + 1];
				arr[j + 1] = temp;
			}
		}
	}
	//排序后的结果
	cout << "排序后：" << endl;
	for (int i = 0; i < 9; i++)
	{
		cout << arr[i] << " ";
	}
	cout << endl;

	system("pause");
	return 0;
}
```

 - 结果

![在这里插入图片描述](https://img-blog.csdnimg.cn/15401eaf43c041218c614b1d6ca7706d.png)	

# 8 二维数组
## 8.1 二维数组定义
二维数组定义的四种方式：

1. ` 数据类型  数组名[ 行数 ][ 列数 ]; `
2. `数据类型  数组名[ 行数 ][ 列数 ] = { {数据1，数据2 } ，{数据3，数据4 } };`
3. `数据类型  数组名[ 行数 ][ 列数 ] = { 数据1，数据2，数据3，数据4};`
4. ` 数据类型  数组名[  ][ 列数 ] = { 数据1，数据2，数据3，数据4};`

![在这里插入图片描述](https://img-blog.csdnimg.cn/a8f3698efad54511b20fa4fa1e6dfaf1.png)

```cpp
#include<iostream>
using namespace std;

int main()
{
	//二维数组定义方式
	/*
		1.数据类型  数组名[行数][列数];
		2.数据类型  数组名[行数][列数] = { {数据1，数据2 } ，{数据3，数据4 } };
		3.数据类型  数组名[行数][列数] = { 数据1，数据2，数据3，数据4 };
		4.数据类型  数组名[][列数] = { 数据1，数据2，数据3，数据4 };
	*/

	//方式1  
	//数组类型 数组名 [行数][列数]
	int arr[2][3];
	arr[0][0] = 1;
	arr[0][1] = 2;
	arr[0][2] = 3;
	arr[1][0] = 4;
	arr[1][1] = 5;
	arr[1][2] = 6;

	for (int i = 0; i < 2; i++)
	{
		for (int j = 0; j < 3; j++)
		{
			cout << arr[i][j] << " ";
		}
		cout << endl;
	}

	//方式2 
	//数据类型 数组名[行数][列数] = { {数据1，数据2 } ，{数据3，数据4 } };
	int arr2[2][3] =
	{
		{1,2,3},
		{4,5,6}
	};

	//方式3
	//数据类型 数组名[行数][列数] = { 数据1，数据2 ,数据3，数据4  };
	int arr3[2][3] = { 1,2,3,4,5,6 };

	//方式4 
	//数据类型 数组名[][列数] = { 数据1，数据2 ,数据3，数据4  };
	int arr4[][3] = { 1,2,3,4,5,6 };

	system("pause");
	return 0;
}
```
## 8.2 二维数组数组名
* **查看二维数组所占内存空间**
* **获取二维数组首地址**

```cpp
#include<iostream>
using namespace std;

int main()
{
	// 二维数组名称用途
	// 1.可以查看占用内存空间大小
	int arr[2][3] =
	{
		{1,2,3},
		{4,5,6}
	};

	cout << "二维数组占用内存空间大小： " << sizeof(arr) << endl;// 24 = 4 * 6
	cout << "二维数组第一行占用内存大小： " << sizeof(arr[0]) << endl;// 12 
	cout << "二维数组第一个元素占用内存大小： " << sizeof(arr[0][0]) << endl;// 4

	cout << "二维数组行数： " << sizeof(arr) / sizeof(arr[0]) << endl;// 2
	cout << "二维数组列数： " << sizeof(arr[0]) / sizeof(arr[0][0]) << endl;// 3

	// 2. 可以查看二维数组的首地址
	cout << "二维数组首地址：" << (int)arr << endl;
	cout << "二维数组第一行首地址：" << (int)arr[0] << endl;
	cout << "二维数组第二行首地址：" << (int)arr[1] << endl;

	cout << "二维数组第一个元素地址：" << (int)&arr[0][0] << endl;
	cout << "二维数组第二个元素地址：" << (int)&arr[0][1] << endl;

	system("pause");
	return 0;
}
```

 - **结果**

![在这里插入图片描述](https://img-blog.csdnimg.cn/76b5fe8ae5084dcb92aff9ec904af854.png)	

 - **总结**
 - 1：二维数**组名就是这个数组的首地址**
 - 2：对**二维数组名进行sizeof**时，可以**获取整个二维数组占用的内存空间大小**

## 8.3 二维数组练习：考试成绩统计
案例描述：有三名同学（张三，李四，王五），在一次考试中的成绩分别如下表，**请分别输出三名同学的总成绩**

|      | 语文 | 数学 | 英语 |
| ---- | ---- | ---- | ---- |
| 张三 | 100  | 100  | 100  |
| 李四 | 90   | 50   | 100  |
| 王五 | 60   | 70   | 80   |

 - 分析

![在这里插入图片描述](https://img-blog.csdnimg.cn/fd7b6b0363fd47aebb9b33b936b8a9fb.png)

```cpp
#include<iostream>
#include<string>
using namespace std;

int main()
{
	//二维数组案例—考试成绩统计

	//1.创建二维数组
	int score[3][3] =
	{
		{100,100,100},
		{90,50,100},
		{60,70,80},
	};

	string name[3] = { "张三","李四","王五" };

	//2.统计每个人的总和分数
	for (int i = 0; i < 3; i++)
	{
		int sum = 0;
		for (int j = 0; j < 3; j++)
		{
			sum += score[i][j];
		}
		cout << name[i] << "同学总成绩为： " << sum << endl;
	}

	system("pause");
	return 0;
}
```

 - 结果

![在这里插入图片描述](https://img-blog.csdnimg.cn/bff82c49599a46ad9e6a1bcb652cf910.png)	

# 9 函数
## 9.1 函数定义
```cpp
返回值类型 函数名 （参数列表）
{
       函数体语句

       return表达式
}
```
函数的定义一般主要有5个步骤

* **返回值类型** ：一个函数可以返回一个值。在函数定义中
* **函数名**：给函数起个名称
* **参数列表**：使用该函数时，传入的数据
* **函数体语句**：花括号内的代码，函数内需要执行的语句
* **return表达式**： 和返回值类型挂钩，函数执行完后，返回相应的数据
![在这里插入图片描述](https://img-blog.csdnimg.cn/371a94ddaa724ce8bfb55832d229d3e8.png)
```cpp
//函数定义
int add(int num1, int num2)
{
	int sum = num1 + num2;
	return sum;
}
```
## 9.2 函数调用
 - 函数名（参数）
 - 函数定义里小括号内称为形参，函数调用时传入的参数称为实参

```cpp
#include<iostream>
using namespace std;

// 函数的定义
// 返回值类型 函数名(参数列表) {函数体语句 return表达式}

// 加法函数，实现两个整数相加，并且返回相加的结果
// 函数定义时，num1和num2并没有真实的数据，只是形式上参数，简称形参
int add(int num1, int num2)// 返回的是整型
{
	int sum = num1 + num2;
	return sum;
}

int main()
{
	int a = 10;
	int b = 20;
	// 函数调用语法：函数名称(参数)
	// a和b是实际的参数，简称实参
	// 调用函数时，实参的值会传递给形参
	int c = add(a, b);
	cout << "c=" << c << endl;
	system("pause");
	return 0;
}
```
## 9.3 值传递(形参无法修改实参)
* 所谓值传递，就是函数调用时实参将数值传入给形参
* 值传递时，==如果形参发生，并不会影响实参==

![在这里插入图片描述](https://img-blog.csdnimg.cn/840be58989704feda21ede13e7ca0dca.png)

```cpp
#include<iostream>
using namespace std;

//值传递（形参变化之后不会改变实参）
//地址传递——形参改变，实参也会改变
//定义函数，实现两个数字进行交换函数

//如果函数不需要返回值，声明时可以写void
void swap(int num1, int num2)
{
	cout << "交换前：" << endl;
	cout << "num1 = " << num1 << endl;
	cout << "num2 = " << num2 << endl;

	int temp = num1;
	num1 = num2;
	num2 = temp;

	cout << "交换后：" << endl;
	cout << "num1 = " << num1 << endl;
	cout << "num2 = " << num2 << endl;
	//return；返回值不需要时可以不写return
}
int main()
{
	int a = 10;
	int b = 20;

	cout << "a = " << a << endl;//a = 10
	cout << "b = " << b << endl;//b = 20

	//当做值传递时，函数的形参发生改变，并不会影响实参
	swap(a, b);

	cout << "a = " << a << endl;//a = 10
	cout << "b = " << b << endl;//b = 20

	system("pause");
	return 0;
}
```

 - 结果

![在这里插入图片描述](https://img-blog.csdnimg.cn/9769593a08a1483c993d5f6181bb40b2.png)	

## 9.4 函数的常见样式
常见的函数样式有4种

1. 无参无返
2. 有参无返
3. 无参有返
4. 有参有返

```cpp
#include<iostream>
using namespace std;

//函数常见样式
//1、 无参无返
void test01()
{
	//void a = 10; //无类型不可以创建变量,原因无法分配内存
	cout << "this is test01" << endl;
	//test01(); 函数调用
}

//2、 有参无返
void test02(int a)
{
	cout << "this is test02" << endl;
	cout << "a = " << a << endl;
}

//3、无参有返
int test03()
{
	cout << "this is test03 " << endl;
	return 10;
}

//4、有参有返
int test04(int a, int b)
{
	cout << "this is test04 " << endl;
	int sum = a + b;
	return sum;
}

int main()
{
	//无参无返函数调用
	test01();

	//有参无返函数调用
	test02(10);

	//无参有返函数调用
	int num1 = test03();
	cout << "num1 = " << num1 << endl;//num1 = 10

	//有参有返函数调用
	int num2 = test04(10, 20);
	cout << "num2 = " << num2 << endl;

	system("pause");
	return 0;
}
```
## 9.5 函数声明
- **作用：** 告诉编译器**函数名称及如何调用函数**。函数的实际主体可以单独定义

 - 函数的**声明可以多次**，但是函数的**定义只能有一次**

```cpp
#include<iostream>
using namespace std;

// 函数的声明
// 比较函数，实现两个整型数字进行比较，返回较大的值

// 提前告诉编译器函数的存在，可以利用函数的声明(如果函数定义在main函数后面)
// 声明可以写多次，定义只能有一次

// 函数的声明(函数往后写，告诉编译器函数存在)
int max(int a, int b);
int max(int a, int b);

// 定义函数
int max(int a, int b)
{
	return a > b ? a : b;
}

int main()
{
	int a = 10;
	int b = 20;

	cout << max(a, b) << endl;

	system("pause");
	return 0;
}
```
## 9.6 函数分文件编写
**作用**：让代码结构更加清晰

函数分文件编写一般有4个步骤

1. 创建后缀名为.h的头文件  
2. 创建后缀名为.cpp的源文件
3. 在`头文件中写函数的声明`
4. 在`源文件中写函数的定义`

程序如下

 - 头文件 swap.h


```cpp
//swap.h文件
#include<iostream>
using namespace std;

//实现两个数字交换的函数声明
void swap(int a, int b);
```

 - 源文件 swap.cpp

```cpp
//swap.cpp文件
#include "swap.h"

void swap(int a, int b)
{
	int temp = a;
	a = b;
	b = temp;

	cout << "a = " << a << endl;
	cout << "b = " << b << endl;
}
```

 - 源文件 main.cpp

```cpp
#include<iostream>
using namespace std;
#include"swap.h" //这样就可以直接在main函数中使用swap函数

//函数的分文件编写
//实现两个数字交换的函数

//函数的声明
//void swap(int a, int b);

//函数的定义
//void swap(int a, int b)
//{
//	int temp = a;
//	a = b;
//	b = temp;
//
//	cout << "a=" << a << endl;
//	cout << "b=" << b << endl;
//}

//一般来说这里只要写main函数
int main()
{
	int a = 10;
	int b = 20;

	swap(a, b);

	system("pause");
	return 0;
}
```

# 基础3 指针、结构体(重难点)

# 10 指针
## 10.1 指针定义和使用
![在这里插入图片描述](https://img-blog.csdnimg.cn/afa33d5b67314c13b957826c9d55b488.png)
> 指针变量定义语法： `数据类型 * 变量名；`指针就是地址

**指针变量和普通变量的区别**

* 普通变量存放的是数据，**指针变量存放的是地址**
* 指针变量可以**通过" * "操作符**，**操作指针变量指向的内存空间**，这个过程称为**解引用**

**要点**

 - 定义指针：数据类型 * 指针变量名
 - 使用指针：通过**“解引用”的方式找到指针指向的内存**，指针前加*号代表解引用，**找到指针指向的内存中的数据**。
 - `*p = 1000`，通过*p**修改内存或者访问内存**

**总结**

 - 1： 我们可以通过 **& 符号 获取变量的地址**
 - 2：利用指针可以记录地址
 - 3：对指针变量解引用，可以操作指针指向的内存

```cpp
// p保存的是一个地址
// 利用指针来保存地址，指针就是一个地址
#include<iostream>
using namespace std;

int main()
{
	// 1.定义指针
	int a = 10;

	// 指针定义的语法：数据类型 * 指针变量名
	int* p;

	// 让指针记录变量a的地址,打印结果一样

	p = &a;		// a的地址存放在变量p中
	cout << "a的地址：" << &a << endl;
	cout << "指针p为：" << p << endl; // p记录a的地址

	// 2.使用指针
	// 可以通过“解引用”的方式找到指针指向的内存
	// 指针前加*号代表解引用，找到指针指向的内存中的数据
	*p = 1000;	// 通过*p修改内存或者访问内存
	cout << "a = " << a << endl;
	cout << "*p = " << *p << endl;

	system("pause");
	return 0;
}
```
运行结果
![在这里插入图片描述](https://img-blog.csdnimg.cn/94c98d9b3ff24ab8ab2a6b7f4591df87.png)
## 10.2 指针所占内存空间
![在这里插入图片描述](https://img-blog.csdnimg.cn/7db31a0a583046d185d1e97f65a5fe2d.png)
 - 所有指针类型在32位操作系统下是4个字节，64位操作系统下是8个字节

```cpp
#include<iostream>
using namespace std;

int main()
{
	//指针占用的空间大小
	int a = 10;
	//int* p;
	//p = &a;//指针指向数据a的地址

	int* p = &a;//等价于int* p; p = &a;

	//在32位操作系统下，指针占4个字节空间大小，不管是什么数据类型
	//在64位操作系统下，指针占8个字节空间大小
	cout << "sizeof(int*) = " << sizeof(int*) << endl;  //sizeof(p) 4
	cout << "sizeof(float*) = " << sizeof(float*) << endl;
	cout << "sizeof(double*) = " << sizeof(double*) << endl;
	cout << "sizeof(char*) = " << sizeof(char*) << endl;

	system("pause");
	return 0;
}
```

 - **结果**

![在这里插入图片描述](https://img-blog.csdnimg.cn/a39bc2ea9ff94c49a46120a1f8380517.png)	

## 10.3 空指针
刚开始不知道指针该指向哪里，初始化有地方可指，后期有地方可指应该重新更改指向。
 - **空指针**：指针变量指向**内存中编号为0的空间**
 - **用途**：**初始化指针变量**
 - **注意**：空指针指向的内存是不可以访问的，**0~255之间的内存编号是系统占用的，因此不可以访问**

```cpp
#include<iostream>
using namespace std;

int main()
{
	// 空指针
	// 1.空指针用于给指针变量进行初始化
	int* p = NULL;// 0是空指针的地址编号

	// 2.空指针是不可以进行访问
	// 0~255之间的内存编号是系统占用的，因此不可以访问
	// *p = 100;// 会报错

	system("pause");
	return 0;
}
```

## 10.4 野指针
 - **野指针**：`指针变量指向非法的内存空间`
 - 空指针和野指针都不是我们申请的空间，因此不要访问

```cpp
#include<iostream>
using namespace std;

int main()
{
	// 野指针：指针变量指向非法的内存空间
	// 程序中，尽量避免野指针
	// 指针变量p指向内存地址编号为0x1100的空间
	int* p = (int*)0x1100;

	// 访问野指针报错 
	cout << *p << endl;

	system("pause");
	return 0;
}
```
## 10.5 const修饰指针(难点)
 - **看const右侧紧跟着的是指针还是常量, 是指针就是常量指针，是常量就是指针常量**

### 10.5.1 常量指针(修饰指针，可以改指针)
 - const修饰指针 —— **常量指针** const int *p = &a
 - 特点：**指针的指向可以修改，但指针指向的值不能修改**
 - **常量指针不能修改的是常量，可以修改指针里面的地址**
 - 如下图所示，a与b中的值都为10，指针p可以指向b，但b中的值必须是10

![在这里插入图片描述](https://img-blog.csdnimg.cn/95e487cd6e4b436b9da29ec5cfa2f30e.png)

```cpp
// 1.const修饰指针——常量指针，常量就是const
	const int* p = &a;//特点：指针的指向可以修改，但指针指向的值不可以修改
	//*p = 20; 错误
	p = &b;//正确
```

### 10.5.2 指针常量(修饰常量，可以改常量)
 - const修饰**常量 —— 指针常量** int * const p = &a
 - 特点：**指针的指向不可以修改，指针指向的值可以修改**
 - **指针常量不可以修改的是指针，可以修改的是常量**
 - 
![在这里插入图片描述](https://img-blog.csdnimg.cn/17eeaf598c2b42eca04fab9e0ae66d35.png)
```cpp
// 2.const修饰常量——指针常量
	//特点：指针的指向不可以修改，指针指向的值可以修改
	int* const p1 = &a;//const后面跟着常量
	*p1 = 20;//正确
	//p = &b;//错误，指针指向不可改
```
### 10.5.3 修饰指针和常量
 - const既修饰指针，又修饰常量
 - 特点：**指针的指向和指针指向的值都不能修改**
![在这里插入图片描述](https://img-blog.csdnimg.cn/6c947011a84c45f6b01e6d0d4c877245.png)

```cpp
//3.const既修饰指针，又修饰常量
	const int* const p2 = &a;//特点：指针的指向和指针指向的值都不可以改
```

```cpp
#include<iostream>
using namespace std;

int main()
{
	int a = 10;
	int b = 10;

	// 1.const修饰指针——常量指针，常量就是const
	const int* p = &a;//特点：指针的指向可以修改，但指针指向的值不可以修改
	// *p = 20; 错误
	p = &b;// 正确

	// 2.const修饰常量——指针常量
	// 特点：指针的指向不可以修改，指针指向的值可以修改
	int* const p1 = &a;// const后面跟着常量
	*p1 = 20;// 正确
	// p = &b;// 错误，指针指向不可改

	// 3.const既修饰指针，又修饰常量
	const int* const p2 = &a;// 特点：指针的指向和指针指向的值都不可以改

	system("pause");
	return 0;
}
```

## 10.6 指针与数组(难点)
 - **作用**：利用指针访问数组中元素
 - **数组名就是数组的首地址，所以可以将首地址赋值给指针**
 - `int* p = arr;	数组名arr就是数组的首地址`
 - `p++ 指向数组下一个位置，指针后移4个字节`

![在这里插入图片描述](https://img-blog.csdnimg.cn/31cf0f63ccfe41ee9839573781dfdd15.png)

```cpp
#include<iostream>
using namespace std;

int main()
{
	// 指针和数组
	// 利用指针访问数组中的元素

	int arr[10] = { 1,2,3,4,5,6,7,8,9,10 };
	cout << "第一个元素为：" << arr[0] << endl;

	int* p = arr;	// 数组名arr就是数组的首地址
	cout << "利用指针访问第一个元素：" << *p << endl;
	p++;	// 让指针向后偏移4个字节
	cout << "利用指针访问第二个元素：" << *p << endl;

	cout << "利用指针遍历数组：" << endl;
	int* p2 = arr;
	for (int i = 0; i < 10; i++)
	{
		// cout << arr[i] << endl;
		cout << *p2 << " ";// p2里面是数组地址，*p2指向地址所在的值
		p2++;
	}
	cout << endl;

	system("pause");
	return 0;
}
```
 - **结果**

![在这里插入图片描述](https://img-blog.csdnimg.cn/d0d7f7b329b7469292c8af2a3d818861.png)	

## 10.7 指针与函数 — 地址传递&(难点)
 - **作用**：利用指针作函数参数，可以修改实参的值
 - 如果不想修改实参，就用值传递，如果**想修改实参，就用地址传递**
 - \*p1、*p2分别表示所在地址的值，**地址传递改变实参本质是地址所在值进行改变**(比如交换)，但指针所指的地址是不变的(值变，地址不变)。
![在这里插入图片描述](https://img-blog.csdnimg.cn/03a8fa0145bc47c09654393b8459f46f.png)

```cpp
#include<iostream>
using namespace std;

// 实现两个数字进行交换
void swap01(int a, int b)// 形参a,b发生改变，实参没有改变
{
	int temp = a;// temp保存的是a的值
	a = b;
	b = temp;

	cout << "swap01 a = " << a << endl;
	cout << "swap01 b = " << b << endl;
}

void swap02(int* p1, int* p2)
{
	// temp保存的是a的值10，*p1保存的是变量a的地址，*p2保存的是变量b的地址
	int temp = *p1;
	*p1 = *p2;
	*p2 = temp;
}

int main()
{
	// 指针和函数
	// 1.值传递(形参改变不了实参)
	int a1 = 10;
	int b1 = 20;
	swap01(a1, b1);

	cout << "a1 = " << a1 << endl;
	cout << "b1 = " << b1 << endl;
	cout << endl;

	// 2.地址传递(形参改变实参)
	// 地址传递可以修饰实参
	int a2 = 10;
	int b2 = 20;
	swap02(&a2, &b2);// p1和p2都要传递地址

	cout << "a2 = " << a2 << endl;
	cout << "b2 = " << b2 << endl;

	system("pause");
	return 0;
}
```

 - **结果**

![在这里插入图片描述](https://img-blog.csdnimg.cn/5aa75dc94ed14cbd9d9c585150087efc.png)	
## 10.8 指针、数组与函数案例(重难点)
**案例描述**：封装一个函数，利用冒泡排序，实现对整型数组的升序排序
						例如数组：int arr[10] = { 4,3,6,9,1,2,10,8,7,5 }

 - **当数组名传入到函数作为参数时，被退化为指向首元素的指针**
 - **把一个数组传递到函数中，就是用指针接收数组首地址！！！！！**

 **超级重点：**
 - **arr单独表示时是指数组的首地址，arr[i] 表示的是数组第i个元素**
 - 同样**指针p单独表示时是指数组的首地址，而p[i]则表示的是数组第i个元素**
 - **指针单独表示就是代表其中的地址值**，**本质上arr和指针p是一个东西**！！！

>   **`非常重要的结论如下`**

 - 下面的int* p等价于int p[ ]；int* q等价于int q[ ]，两种写法是相等的，可以相互替换。一个是用指针传递数组，一个使用数组传递数组。两种写法结果是相等的。

```cpp
#include<iostream>
using namespace std;

//冒泡排序函数  参数1  数组的首地址  参数2  数组的长度
void bubbleSort(int* p, int len)	// arr表示数组的首地址，len是数组的长度
{
	for (int i = 0; i < len - 1; i++) //p本质是一个数组，int* p表示数组第一个元素
	{
		for (int j = 0; j < len - i - 1; j++)
		{
			//如果j > j+1的值，交换数字
			if (p[j] > p[j + 1])
			{
				int temp = p[j];
				p[j] = p[j + 1];
				p[j + 1] = temp;
			}
		}
	}
}

//打印数组
void printArray(int* q, int len)// 传入的是数组的首地址以及数组长度
{
	for (int i = 0; i < len; i++)//q本质是一个数组，int* q表示数组第一个元素
	{
		cout << q[i] << " ";
	}
	cout << endl;
}

int main()
{
	//1.先创建一个数组
	int arr[10] = { 4,3,6,9,1,2,10,8,7,5 };

	//数组长度
	int len = sizeof(arr) / sizeof(arr[0]);

	//2.创建函数，实现冒泡排序(传入数组及其长度)
	bubbleSort(arr, len);// arr就是数组的地址

	//3.打印排序后的数组
	printArray(arr, len);

	system("pause");
	return 0;
}
```
 - 结果

![在这里插入图片描述](https://img-blog.csdnimg.cn/8b079218a8ef4a3b844fa068a520fba2.png)	

# 11 结构体(难点)
## 11.1 结构体定义和使用
**语法：**`struct 结构体名 { 结构体成员列表 }；`最后一定要加封号

通过结构体创建变量的方式有三种：

 * struct 结构体名 变量名
 * struct 结构体名 变量名 = { 成员1值 ， 成员2值...}
 * 定义结构体时顺便创建变量(在写struct最后就可以)不建议用

**总结**
 * 1：**定义**结构体时的关键字是struct，**struct不可省略**
 * 2：**创建**结构体**变量**时，**关键字struct 可以省略**
 * 3：结构体变量利用**操作符 ''.''  访问成员**

```cpp
#include<iostream>
#include<string>
using namespace std;

// 1.创建学生数据类型——学生包括(姓名、年龄、分数)
// 自定义数据类型，一些类型集合组成的一个类型
// 语法  struct 类型名称 {成员列表}
struct Student
{
	// 姓名
	string name;
	// 年龄
	int age;
	// 分数
	int score;
}s3;	// 创建结构体时顺便创建变量

// 2.通过学生类型创建具体的学生(三种创建方式)
int main()
{
	// 2.1 struct Student s1
	// 结构体创建时struct关键字可以省略，结构体定义时struct关键字不可以省略
	struct Student s1;
	// Student s1;这样创建也是可以的
	// 给s1属性赋值，通过“.”访问结构体变量中的属性
	s1.name = "张三";
	s1.age = 18;
	s1.score = 100;

	cout << "姓名：" << s1.name << " 年龄：" << s1.age << " 分数：" << s1.score << endl;

	// 2.2 struct Student s2={...}
	struct Student s2 = { "李四",19,80 };

	cout << "姓名：" << s2.name << " 年龄：" << s2.age << " 分数：" << s2.score << endl;

	// 2.3 定义结构体时顺便创建结构体变量，上面结构体最后写了s3
	s3.name = "王五";
	s3.age = 20;
	s3.score = 80;

	cout << "姓名：" << s3.name << " 年龄：" << s3.age << " 分数：" << s3.score << endl;

	system("pause");
	return 0;
}
```
**结果**
![在这里插入图片描述](https://img-blog.csdnimg.cn/640e2cddfbdf4781a413ae65f203a325.png)
## 11.2 结构体数组

 - **作用**：将自定义的结构体放入到数组中方便维护
 - **语法**：` struct  结构体名 数组名[元素个数] = {  {} , {} , ... {} }`

```cpp
#include<iostream>
#include<string>
using namespace std;

// 结构体数组
// 1.定义结构体
struct Student
{
	// 成员变量
	string name;// 姓名
	int age;// 年龄
	int score;// 分数
};

int main()
{
	// 2.创建结构体数组
	// 类似于struct Student s2={"李四",19,80}
	struct Student stuArray[3] =
	{
		{"张三",18,100},
		{"李四",28,99},
		{"王五",38,66}
	};

	// 3.给结构体数组中的元素赋值，将王五的信息覆盖
	stuArray[2].name = "赵六";
	stuArray[2].age = 80;
	stuArray[2].score = 60;

	// 4.遍历结构体数组
	for (int i = 0; i < 3; i++)
	{
		cout << "姓名：" << stuArray[i].name << " "
			<< "年龄：" << stuArray[i].age << " "
			<< "分数：" << stuArray[i].score << endl;
	}

	system("pause");
	return 0;
}
```

 - 结果

![在这里插入图片描述](https://img-blog.csdnimg.cn/95dae6a90a464ecfb96b5dc0e28d014d.png)	

## 11.3 结构体指针(用—>指属性)
 - **作用**：通过指针访问结构体中的成员
 - 利用操作符 `-> `可以通过**结构体指针访问结构体属性**

```cpp
#include<iostream>
#include<string>
using namespace std;

// 结构体指针
// 通过指针访问结构体中的成员，利用操作符 `- > `可以通过结构体指针访问结构体属性

// 定义学生结构体
struct Student
{
	string name;// 姓名
	int age;// 年龄
	int score;// 分数
};

int main()
{
	// 1.创建学生的结构体变量
	struct Student s = { "张三",18,100 };

	// 2.通过指针指向结构体变量
	struct Student* p = &s;// struct可以省略

	// 3.通过指针访问结构体变量中的数据
	// 通过结构体指针访问结构体中的属性，需要用“->”，即指针通过 -> 操作符可以访问成员
	cout << "姓名：" << p->name << " " << "年龄：" 
		 << p->age << " "  << "分数：" << p->score << endl;

	system("pause");
	return 0;
}
```

 - 结果

![在这里插入图片描述](https://img-blog.csdnimg.cn/231204a8be1241c0a5985c5666f5142e.png)	

## 11.4 结构体嵌套结构体
![在这里插入图片描述](https://img-blog.csdnimg.cn/a6a72eb4b3a042daa064be9bbfbfcc50.png)

**作用：** 结构体中的成员可以是另一个结构体

**例如**：每个老师辅导一个学员，一个老师的结构体中，记录一个学生的结构体

```cpp
#include<iostream>
#include<string>
using namespace std;

// 定义学生结构体
struct student
{
	string name;// 姓名
	int age;// 年龄
	int score;// 分数
};

// 定义老师结构体
struct teacher
{
	int id;// 教师编号
	string name;// 教师姓名
	int age;// 年龄
	struct student stu;// 辅导的学生
};

int main()
{
	// 结构体嵌套结构体
	// 创建老师
	teacher t;
	t.id = 10000;
	t.name = "老王";
	t.age = 50;
	t.stu.name = "小王";// 老师指导的学生
	t.stu.age = 20;
	t.stu.score = 60;

	cout << "老师的姓名：" << t.name << " 老师的编号：" << t.id 
		 << " 老师年龄：" << t.name << endl;
	cout << "辅导学生姓名：" << t.stu.name << " 年龄：" << t.stu.age 
		 << " 考试分数：" << t.stu.score << endl;

	system("pause");
	return 0;
}
```

 - 结果

![在这里插入图片描述](https://img-blog.csdnimg.cn/eea99a91d4fd4000a135489ac1bf2b95.png)

## 11.5 结构体做函数参数(难点)
**作用**：将结构体作为参数向函数中传递

传递方式有两种：

* 值传递
* 地址传递

```cpp
#include<iostream>
#include<string>
using namespace std;

// 定义学生结构体
struct student
{
	string name;// 姓名
	int age;// 年龄
	int score;// 分数
};

// 打印学生信息函数
// 1.值传递   (形参改变不改变实参)
void printStudent1(struct student s)
{
	s.age = 100;// 形参内部打印年龄为100
	cout << "子函数1  姓名：" << s.name << " 年龄：" << s.age 
		 << " 分数：" << s.score << endl;
}

// 2.地址传递  (形参改变可以改变实参)
void printStudent2(struct student* p)// 用指针接收地址，指针地址传递用“->”
{
	p->age = 80;
	cout << "子函数2  姓名：" << p->name << " 年龄：" << p->age 
		 << " 分数：" << p->score << endl;
}

int main()
{
	// 结构体做函数参数
	// 将学生传入到一个参数中，打印学生身上的所有信息

	// 创建结构体变量
	struct student s;
	s.name = "张三";
	s.age = 20;
	s.score = 85;

	// 值传递，age形参值会改变，但实参值不变
	printStudent1(s);
	cout << "main函数 姓名：" << s.name << " 年龄：" << s.age
		 << "  分数：" << s.score << endl;
	cout << endl;

	// 地址传递，age形参值会改变，实参值也会跟着改变
	printStudent2(&s);	
	cout << "main函数 姓名：" << s.name << " 年龄：" << s.age 
		 << " 分数：" << s.score << endl;

	system("pause");
	return 0;
}
```

 - 结果：上面是值传递，下面是地址传递

![在这里插入图片描述](https://img-blog.csdnimg.cn/6a29fd3b4ab5401e91c3e11ec8d6b6ac.png)

## 11.6 结构体const使用
**作用**：用const来防止误操作

```cpp
#include<iostream>
#include<string>
using namespace std;

// const使用场景
// 学生结构体定义
struct student
{
	// 成员列表
	string name;  // 姓名
	int age;      // 年龄
	int score;    // 分数
};

// 将函数中的形参改为指针，可以减少内存空间，而且不会复制新的副本出来
void printStudent(const student* stu) // 加const防止函数体中的误操作
{
	// stu->age = 100; // 加const修饰防止误操作，防止修改
	cout << "姓名：" << stu->name << " 年龄：" << stu->age << " 分数：" 
		 << stu->score << endl;
}// 指针访问用“->”

int main()
{
	student stu = { "张三",18,100 };
	printStudent(&stu);

	system("pause");
	return 0;
}
```

 - 结果：防止结构体数据进行修改，无法使用stu->age = 100进行年龄修改

![在这里插入图片描述](https://img-blog.csdnimg.cn/3fdd66a171124c398ddf5796487f8882.png)	

## 11.7 结构体案例1
**案例描述：**

学校正在做毕设项目，每名老师带领5个学生，总共有3名老师，需求如下：

 - 设计学生和老师的结构体，在老师的结构体中，有老师姓名和一个存放5名学生的**数组**作为成员

 - 学生的成员有姓名、考试分数，创建**数组存放3名老师**，**通过函数给每个老师及所带的学生赋值**

 - 最终打印出老师数据以及老师所带的学生数据
![在这里插入图片描述](https://img-blog.csdnimg.cn/f61bcf73218e49ff96474f231cab133b.png)

 - 这里**struct Teacher tArray[ ]可以用struct Teacher* tArray替代**，使用的是指针，其他的不变。

```cpp
#include<iostream>
#include<string>
#include<ctime>
using namespace std;

//定义学生结构体
struct Student
{
	string sName;//姓名
	int score;//分数
};

//定义老师结构体
struct Teacher
{
	string tName;//教师姓名
	struct Student sArray[5];//学生数组
};

//给老师和学生赋值的函数，使用数组和长度
void allocateSpace(struct Teacher tArray[], int len)
{
	//string nameSeed = "ABCDE";	// 老师3个，每个老师指导5个学生
	char nameSeed[] = "ABCDE";  // 这种方法也可以
	//给老师赋值
	for (int i = 0; i < len; i++)
	{
		tArray[i].tName = "Teacher_";
		tArray[i].tName += nameSeed[i];

		//通过循环给每名老师所带的学生赋值
		for (int j = 0; j < 5; j++)
		{
			tArray[i].sArray[j].sName = "Student_";
			tArray[i].sArray[j].sName += nameSeed[j];
			int random = rand() % 61 + 40;//学生分数在40~100(如果61改为60则范围是40~99)
			tArray[i].sArray[j].score = random;
		}

	}
}

//打印所有信息，使用数组和长度
void printInfo(struct Teacher tArray[], int len)
{
	for (int i = 0; i < len; i++)
	{
		cout << "老师姓名：" << tArray[i].tName << endl;
		for (int j = 0; j < 5; j++)
		{
			cout << "\t学生姓名：" << tArray[i].sArray[j].sName << "  "
				 << " 考试分数：" << tArray[i].sArray[j].score << endl;
		}
		cout << endl;
	}
}

int main()
{
	//随机数种子
	srand((unsigned int)time(NULL));// 加#include<ctime>

	//1.创建3名老师的数组
	struct Teacher tArray[3];

	//2.通过函数给3名老师的信息赋值，并给老师带的学生信息赋值
	int len = sizeof(tArray) / sizeof(tArray[0]);// 这里 len = 3
	allocateSpace(tArray, len);

	//3.打印所有老师及所带的学生信息
	printInfo(tArray, len);

	system("pause");
	return 0;
}
```

 - 结果

![在这里插入图片描述](https://img-blog.csdnimg.cn/089ebf93e65b4cb4a0f529b45eb72e00.png)	

## 11.8 结构体案例2
**案例描述**：设计一个英雄的结构体，包括成员姓名，年龄，性别;创建结构体数组，数组中存放5名英雄。
通过冒泡排序的算法，将数组中的英雄按照年龄进行升序排序，最终打印排序后的结果。

五名英雄信息如下：
```C++
{"刘备",23,"男"},
{"关羽",22,"男"},
{"张飞",20,"男"},
{"赵云",21,"男"},
{"貂蝉",19,"女"},
```

```cpp
#include<iostream>
#include<string>
using namespace std;


//1.设计英雄结构体
struct Hero
{
	string name;//姓名
	int age;//年龄
	string sex;//性别
};

//冒泡排序——实现年龄升序排列
void bubbleSort(struct Hero heroArray[], int len)
{
	for (int i = 0; i < len - 1; i++)
	{
		for (int j = 0; j < len - i - 1; j++)
		{
			//如果j下标的元素年龄大于j+1下标的元素年龄，就交换两个元素
			if (heroArray[j].age > heroArray[j + 1].age)
			{
				struct Hero temp = heroArray[j];//temp是结构体类型
				heroArray[j] = heroArray[j + 1];
				heroArray[j + 1] = temp;
			}
		}
	}
}

//打印排序后数组中的信息
void printHero(struct Hero heroArray[], int len)
{
	for (int i = 0; i < len; i++)
	{
		cout << "姓名：" << heroArray[i].name << " 年龄：" << heroArray[i].age
			<< " 性别：" << heroArray[i].sex << endl;
	}
}

int main()
{
	//2.创建数组存放5名英雄
	struct Hero heroArray[5] =
	{
		{"刘备",23,"男"},
		{"关羽",22,"男"},
		{"张飞",20,"男"},
		{"赵云",21,"男"},
		{"貂蝉",19,"女"},
	};
	int len = sizeof(heroArray) / sizeof(heroArray[0]);

	cout << "排序前打印：" << endl;
	for (int i = 0; i < len; i++)
	{
		cout << "姓名：" << heroArray[i].name << " 年龄：" << heroArray[i].age
			<< " 性别：" << heroArray[i].sex << endl;
	}
	cout << endl;

	//3.对数组进行排序，按照年龄进行升序排列
	bubbleSort(heroArray, len);
	cout << "排序后打印：" << endl;

	//4.将排序后的结果打印输出
	printHero(heroArray, len);

	system("pause");
	return 0;
}
```

 - 结果

![在这里插入图片描述](https://img-blog.csdnimg.cn/992ba1ccd2e248318346e476ce371d7a.png)	

# 核心1 内存分区、引用、函数提高

# 12 内存分区模型
![在这里插入图片描述](https://img-blog.csdnimg.cn/d8f2e1781fdb4fe19d2c8b74947a0c5e.png)

C++程序在执行时，将内存大方向划分为**4个区域**

- **代码区**：存放函数体的二进制代码，由操作系统进行管理

- **全局区**：存放**全局变量**和**静态变量**以及**常量**

- **栈区**：**编译器自动分配释放**, 存放**函数的参数值**，**局部变量**等

- **堆区**：程序员分配和释放，若程序员不释放，程序结束时由操作系统回收

## 12.1 程序运行前
在程序编译后，生成了**exe可执行程序**，**未执行该程序前**分为两个区域

### 12.1.1 代码区
- 存放 CPU 执行的机器指令，二进制的0和1
- 代码区是**共享**的，共享的目的是对于频繁被执行的程序，只需要在内存中有一份代码即可
 - 代码区是**只读**的，使其只读的原因是防止程序意外地修改了它的指令
 - 存放**可执行代码和常量**

### 12.1.2 全局区(全局变量 静态变量 常量)
![在这里插入图片描述](https://img-blog.csdnimg.cn/1bd1659505ea4675940249b816780435.png)

 -  存放**全局变量**、**静态变量**(**普通变量前面加static**)、**常量**(**字符串常量**、**const修饰的全局变量就是全局常量**)
 - **双引号引起来的是字符串常量**
 - **const修饰的全局变量就是全局常量**
 -  该区域的数据在程序结束后由操作系统释放
 - 局部变量、const修饰的局部变量(局部常量)**均不在全局区**

```cpp
#include<iostream>
using namespace std;

//全局变量(在函数体外面)
int g_a = 10;
int g_b = 10;

//2.1 const修饰的全局变量就是全局常量
const int c_g_a = 10;
const int c_g_b = 10;

int main()
{
	//全局区：存放全局变量、静态变量(static)、常量(字符串常量、const修饰的全局变量就是全局常量)
	//局部变量、const修饰的局部变量(局部常量)均不在全局区

	//创建普通局部变量
	int a = 10;
	int b = 10;

	//int表示看十进制
	cout << "局部变量a的地址为：" << (int)&a << endl;//16121436
	cout << "局部变量b的地址为：" << (int)&b << endl;//16121424
	cout << endl;

	cout << "全局变量g_a的地址为：" << (int)&g_a << endl;//10338356
	cout << "全局变量g_b的地址为：" << (int)&g_b << endl;//10338360
	cout << endl;

	//静态变量(在普通变量前面加static，属于静态变量)
	static int s_a = 10;
	static int s_b = 10;

	cout << "静态变量s_a的地址为：" << (int)&s_a << endl;
	cout << "静态变量s_b的地址为：" << (int)&s_b << endl;
	cout << endl;

	//常量
	//1.字符串常量——"hello",用双引号引起来的都是字符串常量
	cout << "字符串常量的地址为：" << (int)&"hello world" << endl;
	cout << endl;

	//2.const修饰变量
	//2.1 const修饰的全局变量
	cout << "const修饰全局常量c_g_a的地址为：" << (int)&c_g_a << endl;
	cout << "const修饰全局常量c_g_b的地址为：" << (int)&c_g_b << endl;
	cout << endl;

	//2.2 const修饰的局部变量
	const int c_l_a = 10;//c~const g~global l~local
	const int c_l_b = 10;

	cout << "const修饰局部常量c_l_a的地址为：" << (int)&c_l_a << endl;
	cout << "const修饰局部常量c_l_b的地址为：" << (int)&c_l_b << endl;
	cout << endl;

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/fe4ab797ed784c8e82a55f078797fb93.png)
 - 可以看到中间的量地址值在一起的，局部变量都在另一块

总结：

* C++中在程序运行前分为全局区和代码区
* 代码区特点是共享和只读
* 全局区中存放**全局变量、静态变量、常量**
* 常量区中存放 const修饰的全局常量 和 字符串常量

## 12.2 程序运行后
### 12.2.1 栈区
 - 由编译器自动分配释放, 存放**函数的参数值，局部变量**等
 - 注意事项：**不要返回局部变量的地址**，**栈区开辟的数据由编译器自动释放**
  - **int 类型的指针返回的是 int 类型的地址**

```cpp
#include<iostream>
using namespace std;

//栈区：由编译器自动分配释放, 存放函数的参数值,局部变量等
//栈区数据的注意事项 —— 不要返回局部变量的地址
//栈区的数据由编译器管理开辟和释放

// int类型的指针返回的是int类型的地址
int* func(int b)//形参数据、局部变量会放在栈区
{
	b = 100;
	int a = 10;//局部变量，存放在栈区，栈区的数据在函数执行完后自动释放
	return &a;//返回局部变量的地址，所以函数体用指针
}

int main()
{
	//接受func函数的返回值
	int* p = func(1);//函数返回的是地址，所以p是地址值

	cout << *p << endl;//第一次可以打印正确的数字，是因为编译器做了保留
	cout << *p << endl;//第二次这个数据就不再保留

	system("pause");
	return 0;
}
```

### 1.2.2 堆区
![在这里插入图片描述](https://img-blog.csdnimg.cn/61b7161d53114964832a7f48cef6eb17.png)


 - 由程序员分配释放，若程序员不释放，程序结束时由操作系统回收
 - 在C++中主要利用**new在堆区开辟内存**
 - 利用**new关键字可以将数据开辟到堆区，将地址值传给指针**

```cpp
#include<iostream>
using namespace std;

//堆区：由编译器自动分配释放, 存放函数的参数值,局部变量等，堆区数据利用new关键字进行开辟内存
int* func()
{
	//利用new关键字可以将数据开辟到堆区，将地址值传给指针
	//指针本质也是局部变量，放在栈上，指针保存的数据放在了堆区
	//指针前加*号代表解引用，找到指针指向的内存中的数据
	int* p = new int(10);//将开辟的内存的编号给指针p，创建好的数据的地址返回给p
	return p;//返回的是指针p，p里面有10的地址，所以func()是指针类型，只有指针类型可以返回地址
}

int main()
{
	//在堆区开辟数据
	int* p = func();//用指针接受函数的返回值，即将地址给p

	cout << *p << endl;///解引用p地址值，输出为10

	system("pause");
	return 0;
}
```
## 12.3 new 操作符
注意new int()语new int[]的区别
> 1.new int[] 是创建一个int型数组，数组大小是在[]中指定
> int * p = new int[3]; 申请一个动态整型数组，数组的长度为[]中的值
> 2.new int()是创建一个int型数，并且用()括号中的数据进行初始化,例如：
> int *p = new int(10); p指向一个值为10的int数。

- 
  C++中**利用new操作符在堆区开辟数据**

- 堆区开辟的数据，由程序员手动开辟，手动释放，**释放利用操作符delete**

- 语法：` new 数据类型`

- 利用**new创建的数据**，会**返回该数据对应的类型的指针**


```cpp
#include<iostream>
using namespace std;

//1.new的语法
int* func()
{
	//在堆区创建整型数据，堆区开辟的数据，由程序员手动开辟，手动释放，释放利用操作符delete
	//new返回的是 该数据类型的指针，即10是整型指针
	//new是什么类型，返回的就是什么类型
	//double * p =new double(10)
	int* p = new int(10);
	return p;//返回指针p
}

void test01()
{
	int* p = func();
	cout << *p << endl;
	cout << *p << endl;
	//堆区的数据，由程序员管理开辟，程序员管理释放
	//如果想释放堆区的数据，利用关键字delete
	delete p;

	//cout << *p << endl;//内存已经释放，再次访问是非法操作，会报错
}

//2.在堆区利用new开辟数据
void test02()
{
	//创建10整型数据的数组，在堆区
	int* arr = new int[10];//[]里面10代表数组有10个元素,返回连续线性空间的首地址，这里new int[10]与new int()是有区别

	for (int i = 0; i < 10; i++)
	{
		arr[i] = i + 100;//赋值100~109
	}
	for (int i = 0; i < 10; i++)
	{
		cout << arr[i] << " ";
	}
	cout << endl;
	//释放堆区数组
	//释放数组时，要加[]才可以
	delete[]arr;
}
int main()
{
	test01();

	test02();

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/af410edb4afc487c8b68ba00b6a627ca.png)	
# 13 引用(重点)
## 13.1 引用基本使用
**作用**：给变量起别名

**语法**： `数据类型 &别名 = 原名`

![在这里插入图片描述](https://img-blog.csdnimg.cn/d1b2acd1a17f4938be6df29b6c3078ac.png)

```cpp
#include<iostream>
using namespace std;

int main()
{
	//引用基本语法：数据类型 &别名=原名
	//引用就是给变量起别名，

	int a = 10;//占用4个字节
	//创建引用
	int& b = a;//a和b操作同一块内存

	cout << "a=" << a << endl;//10
	cout << "b=" << b << endl;//10

	b = 100;
	cout << "a=" << a << endl;//100
	cout << "b=" << b << endl;//100

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/725014c6818c4decb220e02c311243a9.png)	
## 13.2 引用注意事项
* 引用必须初始化
* 引用在初始化后，不可以改变
* 可以使用赋值进行值得改变

```cpp
#include<iostream>
using namespace std;

int main()
{
	int a = 10;

	//1.引用必须初始化 
	// int &b; //错误，必须要初始化
	int& b = a;
	cout << "a = " << a << " ";//10
	cout << "b = " << b << " ";//10

	//2.引用初始化后就不能更改
	int c = 20;
	//int& c = a; //一旦初始化后，就不可以更改
	b = c; //赋值操作，而不是更改引用

	cout << "a = " << a << " ";//20
	cout << "b = " << b << " ";//20
	cout << "c = " << c << endl;//20

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/67fbfb276a80401195db13abf55738cb.png)	
## 13.3 引用做函数参数-引用传递(重点)

 - **作用**：函数传参时，可以利用引用的技术让形参修饰实参
 - **优点**：可以简化指针修改实参
 - **总结**：通过引用参数产生的效果同按地址传递是一样的。引用的语法更清楚简单

```cpp
#include<iostream>
using namespace std;

//函数传参时，可以利用引用的技术让形参修饰实参。可以简化指针修改实参

//1. 值传递 —— 形参不会修饰实参
void mySwap01(int a, int b)
{
	int temp = a;
	a = b;
	b = temp;

	//cout << "swap01 a=" << a << endl;//a=20
	//cout << "swap01 b=" << b << endl;//b=10
}

//2. 地址传递 —— 形参会修饰实参
void mySwap02(int* a, int* b) //利用指针接收地址
{
	int temp = *a;
	*a = *b;
	*b = temp;
}

//3. 引用传递 —— 形参会修饰实参
void mySwap03(int& a, int& b)
{
	int temp = a;
	a = b;
	b = temp;
}

int main()
{
	int a = 10;
	int b = 20;

	mySwap01(a, b);//值传递形参不会修饰实参
	cout << "a = " << a << " ";//a=10
	cout << "b = " << b << endl;//b=20

	mySwap02(&a, &b);//地址传递形参会修饰实参
	cout << "a = " << a << " ";//a=20
	cout << "b = " << b << endl;//b=10

	//别名可以和原名一样，对形参a的任何修改都会对实参a产生影响，两个a操作同一块内存
	mySwap03(a, b);//引用传递形参会修饰实参
	cout << "a = " << a << " ";// a=10
	cout << "b = " << b << endl;// b=20

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/d030350b31504b70922b3aa1d3fdfb6a.png)	
## 13.4 引用做函数返回值(返回值是引用，可做左值)

 - **作用**：引用是可以作为函数的返回值存在的
 - 注意：**不要返回局部变量引用**
 - **用法**：**函数调用作为左值**
 - **如果函数的返回值是引用，这个函数调用可以作为左值**

```cpp
#include<iostream>
using namespace std;

//引用做函数的返回值
//1.不要返回局部变量的引用
int& test01()//以引用的方式返回变量a
{
	//局部变量存放在四区中的栈区，由编译器自动分配释放, 存放函数的参数值,局部变量等
	int a = 10;
	return a;//返回的是a的别名
}

//2.函数的调用可以作为左值
int& test02()
{
	//静态变量存放在全局区，全局区的数据在程序结束后系统释放
	static int a = 10;
	return a;
}

int main()
{
	int& ref1 = test01();//将a的别名赋给ref

	cout << "ref1 = " << ref1 << " \t";//第一次结果正确，因为编译器做了保留
	cout << "ref1 = " << ref1 << endl;//第二次结果错误，因为a的内存已经释放

	int& ref2 = test02();
	cout << "ref2 = " << ref2 << " \t";//10
	cout << "ref2 = " << ref2 << endl;//10

	//如果函数的返回值是引用，这个函数调用可以作为左值
	test02() = 1000;//返回的是a的引用，相当于直接对原名a进行操作，ref2是a的别名
	cout << "ref2 = " << ref2 << " \t";//1000
	cout << "ref2 = " << ref2 << endl;//1000

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/edb7313539704f6a84d594f781e69e0e.png)
## 13.5 引用的本质

 - 本质：**引用的本质在c++内部实现是一个指针常量**
 - 指针常量，修饰的是常量，**可以修改常量，指针指向的地址是确定的，不能修改的**
 - C++推荐用引用技术，因为语法方便，引用本质是指针常量，但是所有的指针操作编译器都帮我们做了
![在这里插入图片描述](https://img-blog.csdnimg.cn/13842ccf5c84403faff1c510e269e39d.png)

```cpp
#include<iostream>
using namespace std;

//发现是引用，转换为 int* const ref = &a;
//引用的本质是一个指针常量，指针的指向不可以修改，指针指向的值可以修改
void func(int& ref)
{
	ref = 100; // ref是引用，转换为*ref = 100
}
int main()
{
	int a = 10;

	//自动转换为 int* const ref = &a; 指针常量是指针指向不可改，也说明为什么引用不可更改
	int& ref = a;
	ref = 20; //内部发现ref是引用，自动帮我们转换为: *ref = 20;

	cout << "a: " << a << " ";
	cout << "ref: " << ref << endl;

	func(a);
	cout << "a: " << a << " ";
	cout << "ref: " << ref << endl;

	system("pause");
	return 0;
}
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/f55d0d87445245f1af70817eae9b398f.png)
## 13.6 常量引用

 - **作用**：常量引用主要用来修饰形参，防止误操作
 - 在函数形参列表中，可以加==const修饰形参，防止形参改变实参==


```cpp
#include<iostream>
using namespace std;

//打印数据函数(重点)
void showValue(const int& val) //修饰形参，防止形参被修改，这样形参就不会改变实参
{
	//val = 1000;加了const之后val就不能再重新赋值了
	cout << "val = " << val << endl;
}

int main()
{
	//常量引用
	//使用场景：用来修饰形参，防止误操作

	//int& ref = 10;是不合法的
	//int a = 10;
	//int& ref = a;//引用必须引一块合法的内存空间
	
	//加上const后，编译器将代码改为 int temp=10；const int &ref=temp;
	//const int& ref = 10;//引用必须引一块合法的内存空间
	//ref = 20;//加入const后变为只读，不可以修改

	int a = 100;
	showValue(a);

	cout << "a = " << a << endl;// 100，加了const之后，就不能在对val(a)进行修改

	system("pause");
	return 0;
}
```

 - 加const之后在函数体里就不能修改数据

![在这里插入图片描述](https://img-blog.csdnimg.cn/c175781d173c4ef88b6604d18c67ad64.png)
# 14 函数提高
## 14.1 函数默认参数

 - 在C++中，函数的形参列表中的形参是可以有默认值的
 - 语法：` 返回值类型  函数名 （参数= 默认值）{}`
 - **函数声明和实现只能有一个可以有默认参数**

```cpp
#include<iostream>
using namespace std;

//函数的默认参数

//如果我们自己传入了数据，就用自己的数据，如果没有，就用默认值
//语法：返回值类型 函数名(形参=默认值){}
int func1(int a, int b = 20, int c = 30)//如果b有默认参数，则c也必须有默认参数
{
	return a + b + c;
}

int func3(int a, int b, int c)
{
	return a + b + c;
}

//注意事项
//1.如果某个位置已经有了默认参数，那么从这个位置以后，从左到右都必须有默认值 

//2.如果函数的声明有默认参数，函数实现就不能有默认参数
//声明和实现只能有一个有默认参数
int func2(int a = 10, int b = 10);//函数的声明

int func2(int a, int b)
{
	return a + b;//函数的实现
}

int main()
{
	cout << "func1 = " << func1(10) << endl;// 60

	cout << "func3 = " << func3(20, 30, 30) << endl;// 80

	cout << "func2 = " << func2(20) << endl;//30 优先使用自己传入的数据

	system("pause");
	return 0;
}
```
 - 结果

![在这里插入图片描述](https://img-blog.csdnimg.cn/7e44284f2c4b45ce8559e1d11779aee9.png)
## 14.2 函数占位参数

 - C++中函数的形参列表里可以**有占位参数，用来做占位，调用函数时必须填补该位置**
 - **语法：** `返回值类型 函数名 (数据类型){}`
 - 在现阶段函数的占位参数存在意义不大，但是后面的课程中会用到该技术

```cpp
#include<iostream>
using namespace std;

//占位参数(第二个int起到占位作用)
//返回值类型 函数名(数据类型) {}

//占位参数还可以有默认参数
void func(int a, int)
{
	cout << "this is func " << endl;
}

int main()
{

	func(10, 20); //占位参数必须填补, 20必须传入

	system("pause");
	return 0;
}
```
## 14.3 函数重载基本语法(重难点)
- **作用：**函数名可以相同，提高复用性

**函数重载满足条件：**

* **同一个作用域**下：在全局作用域下
* **函数名称相同**：void func()
* 函数参数**类型不同**  或者 **个数不同** 或者 **顺序不同**

**注意:**  函数的**返回值**不可以作为函数重载的条件，第1个是void，第2个是int，不是重载

```cpp
void func(int a, double b)
{
	cout << "func(int a,double b)的调用" << endl;
}

//注意事项
//函数的返回值不可以作为函数重载的条件
//int func(int a, double b)
//{
//	cout << "func(int a,double b)的调用" << endl;
//}
```

```cpp
#include<iostream>
using namespace std;

//函数重载 —— 函数名相同
//可以让函数名相同，提高复用性

//函数重载的而满足条件
//1.同一个作用域下(全局作用域)
//2.函数名称相同
//3.函数参数类型不同，或者个数不同，或者顺序不同
void func()
{
	cout << "func的调用" << endl;
}

void func(int a)
{
	cout << "func(int a)的调用" << endl;
}

void func(int a, double b)
{
	cout << "func(int a,double b)的调用" << endl;
}


//注意事项
//函数的返回值不可以作为函数重载的条件
//int func(int a, double b)
//{
//	cout << "func(int a,double b)的调用" << endl;
//}


int main()
{

	func();
	func(10);
	func(10, 3.14);

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/5bd8fd9ab36a4d4d904ae92c94531596.png)	
## 14.4 函数重载注意事项
* 引用作为重载条件
* 函数重载碰到函数默认参数

```cpp
#include<iostream>
using namespace std;

//函数重载的注意事项
//1.引用作为重载的条件
void func1(int& a)	//int &a = 10;不合法
{
	cout << "func1(int &a)的调用" << endl;
}

void func2(const int& a)//const只读，const int &a = 10;合法
{
	cout << "func2(const int &a)的调用" << endl;
}


//2.函数重载碰到默认参数
void func3(int a, int b)
{
	cout << "func3(int a, int b)的调用" << endl;
}

//函数返回值不可以作为函数重载条件
//int func(double a, int b)
//{
//	cout << "func (double a ,int b)的调用！" << endl;
//}


int main()
{
	int a = 10;
	func1(a); //调用第一个，只能传入a，不能传入10

	func2(10);//调用第二个

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/4124cfaa57cf49459cb1c70fc3b2d409.png)	

# 核心2 类和对象__封装(重难点)

# 15 封装
## 15.1 封装的意义
封装是C++面向对象三大特性之一
封装的意义：

 * **将属性和行为作为一个整体，表现生活中的事物**
 * **将属性和行为加以权限控制**
 * 类中的属性和行为统一称为“成员”
 * 属性   成员属性(成员变量)
 * 行为   成员函数(成员方法)

### 15.1.1 意义一
 * 在设计类的时候，**属性和行为写在一起，表现事物**
 * **语法：** `class 类名{   访问权限： 属性  / 行为  };`
 * **示例1**：设计一个圆类，求圆的周长
#### 求圆周长

```cpp
#include<iostream>
using namespace std;

//圆周率
const double PI = 3.14;

//设计一个圆类，求圆的周长
//圆求周长的公式：2 * PI * 半径

//class代表设计一个类，类后面紧跟着就是类的名称
class Circle
{
	//访问权限
	//公共权限
public:

	//类中的属性和行为统一称为“成员”
	//属性   成员属性(成员变量)
	//行为   成员函数(成员方法)

	//属性 —— 使用变量
	//半径
	int m_r;

	//行为 —— 使用函数
	//获取圆的周长
	double calculateZC()
	{
		return 2 * PI * m_r;
	}
};

int main()
{
	//通过圆类，创建一个具体的圆(对象)
	//实例化——通过一个类创建一个对象的过程
	Circle c1;

	//给圆对象的属性进行赋值
	c1.m_r = 10;

	//调用函数,调用函数行为
	//2 * PI * 10 = 62.8
	cout << "圆的周长为：" << c1.calculateZC() << endl;

	system("pause");
	return 0;
}
```
#### 设计学生类

```cpp
#include<iostream>
#include<string>
using namespace std;

//设计一个学生类，属性有姓名和学号，可以给姓名和学号赋值，可以显示学生的姓名和学号(两个行为)

//设计学生类
class Student
{
	//公共权限
public:
	//类中的属性和行为 我们统一成为 成员
	//属性   成员属性(成员变量)
	//行为   成员函数(成员方法)

	//属性
	string m_name;//姓名
	int m_id;//学号

	//通过行为给属性赋值
	//给姓名赋值
	void setName(string name)
	{
		m_name = name;
	}

	//给学号赋值
	void setId(int id)
	{
		m_id = id;
	}

	//行为
	//显示姓名和学号
	void showStudent()
	{
		cout << "姓名：" << m_name << "学号" << m_id << endl;
	}
};


int main()
{
	//创建一个具体的学生，实例化对象
	Student s1;

	//给s1对象，进行属性赋值操作
	s1.setName("张三");
	s1.setId(1);

	//显示学生信息
	s1.showStudent();

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/a7afed9ac2e443be9fb63556d6422e6d.png)
### 15.1.2 意义二 访问权限

 - **公共权限  public**     类内可以访问  类外可以访问
 - **保护权限  protected**  类内可以访问  类外不可以访问
 - **私有权限  private**    类内可以访问  类外不可以访问

```cpp
#include<iostream>
using namespace std;

//访问权限
//公共权限 public		成员(包括成员函数、属性)类内可以访问，类外也可以访问
//保护权限 protected	    成员类内可以访问，类外不可以访问  儿子可以访问父亲中的保护内容
//私有权限 private		成员类内可以访问，类外不可以访问  儿子不可以访问父亲的私有内容
//保护和私有权限的区别在继承中体现

class Person
{
public:
	//公共权限
	string m_Name;//姓名

protected:
	//保护权限
	string m_Car;//汽车

private:
	//私有权限
	int m_Password;//密码

public://公共函数 下面三个的赋值都属于类内，可以访问
	void func1()
	{
		m_Name = "张三";
		m_Car = "拖拉机";
		m_Password = 123456;
	}

private://私有函数，类内可以访问，类外不可以访问
	void func2()
	{
		m_Name = "张三";
		m_Car = "拖拉机";
		m_Password = 123456;
	}
};


int main()
{
	//实例化具体对象
	Person p1;

	p1.m_Name = "李四";//可以访问，可以进行修改
	//p1.m_Car = "奔驰";//保护权限内容，类外访问不到
	//p1.m_Password = 123;//私有权限内容，类外访问不到

	p1.func1();//public可以访问函数
	//p1.func2();private不可以访问

	system("pause");
	return 0;
}
```
## 15.2 struct 与 classs 的区别(默认访问权限不同)

 - 在C++中 struct和class唯一的**区别**就在于 **==默认的访问权限不同==**
区别：

 - **struct** 默认权限为**公共**
 - **class**   默认权限为**私有**

```cpp
#include<iostream>
using namespace std;

class C1
{
	int m_A;//默认权限是私有
};

struct C2
{
	int m_A;//默认权限是公共
};

int main()
{

	//struct默认权限是 公共 class
	//class默认权限是 私有 private
	C1 c1;
	//c1.m_A = 10;//无法访问，class默认权限是私有

	C2 c2;
	c2.m_A = 10;//可以访问，struct默认权限是公共

	system("pause");
	return 0;
}
```
## 15.3 成员属性设为私有(行为设置和获取分开写 重点)
**优点1**: 将所有成员属性设置为私有，可以自己控制读写权限

**优点2**: 对于写权限，我们可以检测数据的有效性

 - 读：void set(参数类型 xxx) m_xxx = xxxx
 - 写：参数类型 get()  return m_xxx；

分类

 - 又读又写

```cpp
    //设置姓名  写姓名
	void setName(string name)
	{
		m_Name = name;
	}

	//获取姓名  读姓名
	string getName()//返回string类型的字符串
	{
		return m_Name;
	}
```

 - 只读
```cpp
	//获取年龄 只读
	int getAge()	//返回int类型
	{
		m_age = 0;// 初始化为0岁,这样的话最终的年龄还是0岁这样就是只读
		return m_age;
	}
```
 - 只写

```cpp
	//设置情人  只写 —— 外界访问不到该数据
	void setLover(string lover)
	{
		m_Lover = lover;
	}
```

```cpp
#include<iostream>
#include<string>
using namespace std;

//成员属性设置为私有
//1.可以自己控制读写权限
//2.对于写可以检测数据的有效性

//设计人类
class Person
{
public:
	//设置姓名  写姓名
	void setName(string name)
	{
		m_Name = name;
	}

	//获取姓名  读姓名
	string getName()//返回string类型的字符串
	{
		return m_Name;
	}

	//设置年龄 只写
	void setAge(int age)
	{

		if (age < 0 || age>150)
		{
			m_age = 0;
			cout << "你这个老妖精" << endl;
			return;
		}
		m_age = age;
	}

	//获取年龄 只读
	int getAge()	//返回int类型
	{
		m_age = 0;// 初始化为0岁,这样的话最终的年龄还是0岁这样就是只读
		return m_age;
	}

	//设置情人  只写 —— 外界访问不到该数据
	void setLover(string lover)
	{
		m_Lover = lover;
	}

private:
	//姓名	可读可写
	string m_Name;

	//年龄	只读
	int m_age;

	//情人	只写
	string m_Lover;
};

int main()
{
	Person p;
	p.setName("张三");//输入写姓名

	cout << "姓名： " << p.getName() << endl;//输出读姓名

	p.setAge(18);//输入写年龄

	cout << "年龄： " << p.getAge() << endl;//输出读年龄

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/5edc5f67ea994f4396269735136d9fd9.png)
## 15.4 案例1 设计立方体类(重点)
![在这里插入图片描述](https://img-blog.csdnimg.cn/35adcd78430441c4b25962fe1d07aa4b.png)


 - 设计立方体类(Cube)，求出立方体的面积和体积，分别用全局函数和成员函数判断两个立方体是否相等
 - **属性设置为私有，行为设置为公共**

步骤
1. 创建立方体的类
2. 设计属性(私有权限)
3. 设计行为	获取立方体面积和行为
4. 分别利用全局函数和成员函数 判断两个立方体是否相等

三个属性的设置(void set)与获取(int return)
```cpp
//行为
	//设置长
	void setL(int l)
	{
		m_L = l;
	}

	//获取长
	int getL()
	{
		return m_L;
	}

	//设置宽
	void setW(int w)
	{
		m_W = w;
	}

	//获取宽
	int getW()
	{
		return m_W;
	}

	//设置高
	void setH(int h)
	{
		m_H = h;
	}

	//获取高
	int getH()
	{
		return m_H;
	}

	//获取立方体的面积
	int calculateS()
	{
		return 2 * m_L * m_W + 2 * m_W * m_H + 2 * m_L * m_H;
	}

	//获取立方体的体积
	int calculateV()
	{
		return m_H * m_L * m_W;
	}
```

 - 利用**成员函数**判断 两个立方体是否相等（在clsss里面设置函数）

```cpp
//利用成员函数判断两个立方体是否相等
	bool isSameByClass(Cube& c)
	{
		//判断自身的长和传进来的长进行比较
		if (m_L == c.getL() && m_H == c.getH() && m_W == c.getW())
		{
			return true;
		}
		return false;
	}
```

 - 利用**全局函数**判断 两个立方体是否相等

```cpp
bool isSame(Cube& c1, Cube& c2)	//利用引用的方式传递
{
	//长宽高均相等
	if (c1.getL() == c2.getL() && c1.getH() == c2.getH() && c1.getW() == c2.getW())
	{
		return true;
	}
	return false;
}
```

 - 完整代码

```cpp
#include<iostream>
using namespace std;

//1.创建立方体的类
//2.设计属性
//3.设计行为	获取立方体面积和行为
//4.分别利用全局函数和成员函数 判断两个立方体是否相等

class Cube
{
public:

	//行为
	//设置长
	void setL(int l)
	{
		m_L = l;
	}
	//获取长
	int getL()
	{
		return m_L;
	}
	//设置宽
	void setW(int w)
	{
		m_W = w;
	}
	//获取宽
	int getW()
	{
		return m_W;
	}
	//设置高
	void setH(int h)
	{
		m_H = h;
	}
	//获取高
	int getH()
	{
		return m_H;
	}
	//获取立方体的面积
	int calculateS()
	{
		return 2 * m_L * m_W + 2 * m_W * m_H + 2 * m_L * m_H;
	}
	//获取立方体的体积
	int calculateV()
	{
		return m_H * m_L * m_W;
	}
	//利用成员函数判断两个立方体是否相等
	bool isSameByClass(Cube& c)
	{
		//判断自身的长和传进来的长进行比较
		if (m_L == c.getL() && m_H == c.getH() && m_W == c.getW())
		{
			return true;
		}
		return false;
	}

private:
	//属性
	int m_L;//长
	int m_W;//宽
	int m_H;//高
};

//利用全局函数判断 两个立方体是否相等
bool isSame(Cube& c1, Cube& c2)	//利用引用的方式传递
{
	if (c1.getL() == c2.getL() && c1.getH() == c2.getH() && c1.getW() == c2.getW())//长宽高均相等
	{
		return true;
	}
	return false;
}


int main()
{
	//创建立方体对象
	Cube c1;
	c1.setL(10);
	c1.setH(10);
	c1.setW(10);

	//创建第二个立方体
	Cube c2;
	c2.setL(10);
	c2.setH(10);
	c2.setW(10);

	//创建第三个立方体
	Cube c3;
	c3.setL(20);
	c3.setH(30);
	c3.setW(40);

	cout << "c1 的面积为：" << c1.calculateS() << endl;
	cout << "c1 的体积为：" << c1.calculateV() << endl;

	// 使用全局函数判断
	bool ret1 = isSame(c1, c2);
	if (ret1)
	{
		cout << "全局函数 c1 和 c2 相等" << endl;
	} else {
		cout << "全局函数 c1 和 c2 不相等" << endl;
	}

	//利用成员函数判断
	bool ret2 = c1.isSameByClass(c2);//c1为已知立方体，再传入调用c2，进行对比
	if (ret2)
	{
		cout << "成员函数 c1 和 c2 相等" << endl;
	} else {
		cout << "成员函数 c1 和 c2 不相等" << endl;
	}

	bool ret3 = c1.isSameByClass(c3);
	if(ret3)
	{
		cout << "成员函数 c1 和 c3 相等" << endl;
	} else {
		cout << "成员函数 c1 和 c3 不相等" << endl;
	}

	system("pause");
	return 0;
}
```
结果
![在这里插入图片描述](https://img-blog.csdnimg.cn/8d86f5a281364d409b5b88c1110ff3fc.png)
## 15.5 案例2 点和圆的关系(分头、源文件)

 - 设计一个圆形类（Circle），和一个点类（Point），计算点和圆的关系
![在这里插入图片描述](https://img-blog.csdnimg.cn/3b1bdbd5916d419ab3d51a79fd8f6fc8.png)
 - 点类


```cpp
// 点类
class Point
{
public:
	//设置X
	void setX(int x)
	{
		m_X = x;
	}
	//获取X
	int getX()
	{
		return m_X;
	}
	//设置Y
	 void setY(int y)
	{
		m_Y = y;
	}
	//获取Y
	 int getY()
	 {
		 return m_Y;
	 }

private:
	int m_X;
	int m_Y;
};
```

 - 圆类

```cpp
class Circle
{
public:
	//设置半径
	void setR(int r)
	{
		m_R = r;
	}
	//获取半径
	int getR()
	{
		return m_R;
	}
	//设置圆心
	void setCenter(Point center)
	{
		m_Center = center;
	}
	//获取圆心, Point表示返回数据的类型
	Point getCenter()
	{
		return m_Center;
	}

private:
	int m_R;// 半径

	Point m_Center;// 圆心
};
```
###  15.5.1 使用头文件和源文件分写(重点)
 - **头文件 point.h  点类申明**

```cpp
//防止头文件重复包含
#pragma once 
#include<iostream>
using namespace std;

//只需要成员函数申明和变量申明
//点类
class Point
{
public:
	//设置X
	void setX(int x);
	
	//获取X
	int getX();
	
	//设置Y
	void setY(int y);
	
	//获取Y
	int getY();

private:
	int m_X;
	int m_Y;
};
```

 - **源文件 point.cpp 点类实现**
 - **point::**

```cpp
#include"point.h"

//添加Point::,告诉Point作用域的成员函数
//设置X
void Point::setX(int x)
{
	m_X = x;
}
//获取X
int Point::getX()
{
	return m_X;
}
//设置Y
void Point::setY(int y)
{
	m_Y = y;
}
//获取Y
int Point::getY()
{
	return m_Y;
}
```
 - **头文件 ciecle.h 圆类声明**

```cpp
#pragma once 
#include<iostream>
#include"point.h"
using namespace std;

//只做成员函数和变量声明，不做实现
class Circle
{
public:
	//设置半径
	void setR(int r);

	//获取半径
	int getR();
	
	//设置圆心
	void setCenter(Point center);
	
	//获取圆心, Point表示返回数据的类型
	Point getCenter();
	
private:
	int m_R;// 半径

	//在类中可以让另一个类 作为本类的成员
	Point m_Center;// 圆心
};
```

 - **源文件 circle.cpp 圆类实现**
 - **添加 Circle::**

```cpp
#include"circle.h"

//添加类class,只留下函数实现
//设置半径
void Circle::setR(int r)
{
	m_R = r;
}
//获取半径
int Circle::getR()
{
	return m_R;
}
//设置圆心
void Circle::setCenter(Point center)
{
	m_Center = center;
}
//获取圆心, Point表示返回数据的类型
Point Circle::getCenter()
{
	return m_Center;
}
```

 - **主函数源文件main.cpp**

```cpp
#include<iostream>
using namespace std;
#include"point.h"
#include"circle.h"

// 判断点和圆心的关系
void isInCircle(Circle& c, Point& p)
{
	//计算两点之间的距离 平方
	int distance =
		(c.getCenter().getX() - p.getX()) * (c.getCenter().getX() - p.getX()) +
		(c.getCenter().getY() - p.getY()) * (c.getCenter().getY() - p.getY());
	
	//计算半径的平方
	int rDistance = c.getR() * c.getR();

	//判断关系
	if (distance == rDistance)
	{
		cout << "点在圆上" << endl;
	}
	else if (distance > rDistance)
	{
		cout << "点在圆外" << endl;
	}
	else
	{
		cout << "点在圆内" << endl;
	}
}

int main()
{
	// 创建圆
	Circle c;
	c.setR(10);
	Point center;
	center.setX(10);
	center.setY(0);
	c.setCenter(center);

	// 创建点
	Point p;
	p.setX(10);
	p.setY(10);

	// 判断
	isInCircle(c, p);

	system("pause");
	return 0;
}
```

# 核心3 类和对象__对象的初始化和清理(重难点)

 *  生活中我们买的电子产品都基本会有出厂设置，在某一天我们不用时候也会删除一些自己信息数据保证安全
*  C++中的面向对象来源于生活，每个对象也都会有初始设置以及 对象销毁前的清理数据的设置

# 16 构造函数(初始化)和析构函数(清理)
对象的**初始化和清理**也是两个非常重要的安全问题

- 一个**对象或者变量没有初始状态**，对其**使用后果未知**
- 同样的使用完一个对象或变量，没有及时清理，也会造成一定的安全问题

C++利用**构造函数**和**析构函数**解决上述问题，这两个函数将会被编译器自动调用，**完成对象初始化和清理工作**

对象的初始化和清理工作是编译器强制要我们做的事情，因此如果**我们不提供构造和析构，编译器会提供**

> **编译器提供的构造函数和析构函数是空实现**

 - **构造函数**：主要作用在于**创建对象时为对象的成员属性赋值**，构造函数由编译器自动调用，无须手动调用。
 - **析构函数**：主要作用在于对象**销毁前**系统自动调用，执行一些清理工作。

> **构造函数语法：**`类名(){}`

1. 构造函数，没有返回值也不写void
2. **函数名称与类名相同**
3. **构造函数可以有参数**，因此**可以发生重载**
4. 程序在调用对象时候会自动调用构造，无须手动调用,而且只会调用一次

> **析构函数语法：** `~类名(){}`

1. 析构函数，没有返回值也不写void
2. **函数名称与类名相同，在名称前加上符号  ~**
3. **析构函数不可以有参数**，因此**不可以发生重载**
4. 程序在对象销毁前会自动调用析构，无须手动调用,而且只会调用一次

```cpp
#include<iostream>
using namespace std;

//对象的初始化和清理
class Person
{
public:
	//1. 构造函数(写作用域)，进行初始化操作
	//没有返回值，不用写void
	//函数名 与类的名称相同
	//构造函数可以有参数，可以发生重载
	//创建对象时，构造函数会自动调用，而且只调用一次
	Person()
	{
		cout << "Person 构造函数的调用" << endl;

	}
	//2. 析构函数  进行清理操作
	//没有返回值 不写void
	//函数名和类名相同，在名称前加~
	//析构函数不可以有参数，不可以发生重载
	//对象在销毁前，会自动调用析构函数，而且只会调用一次
	~Person()
	{
		cout << "Person 析构函数调用" << endl;
	}

};

//析构和构造都是必须有的实现，如果我们自己不提供，编译器会提供一个空实现的构造和析构函数(没有代码)
void test01()
{
	Person p;//局部变量，在栈上的数据，test01执行完毕后自动释放这个对象
}


int main()
{
	test01();//有构造和析构，在函数调用完之后，对象就会释放，调用析构函数

	cout << endl;

	Person p;//只有构造没有析构，因为对象没有释放，所以没有析构

	system("pause");
	return 0;
}
```

 - 在main函数中 Person p执行完会先调用构造函数，当最后return 0执行结束才会调用析构函数(**对象函数结束销毁就会执行析构函数**)
 - test01()中执行完Person p后，会立马释放这个对象，执行析构函数

![在这里插入图片描述](https://img-blog.csdnimg.cn/6612c8063204495ea10402bb0c3753b0.png)	
# 17 构造函数的分类及调用
## 17.1 分类 — 按参数
 - 无参构造(默认)
```cpp
//无参构造函数
	Person()
	{
		cout << "Person的无参构造函数的调用" << endl;
	}
```
 - 有参构造

```cpp
//有参构造函数
	Person(int a)
	{
		age = a;
		cout << "Person的有参构造函数的调用" << endl;
	}
```

## 17.2 分类 — 按类型(拷贝构造!加引用)
 - 普通构造
 - 拷贝构造

```cpp
//拷贝构造函数
	Person(const Person& p)//拷贝一模一样的数据出来
	{
		//将传入的人身上所有属性，拷贝到我身上
		age = p.age;
	}
```

## 17.3 调用 — 括号法(推荐)
 - 括号法
```cpp
	//1.括号法
	Person p;//默认构造函数调用
	Person p0(10);//有参构造函数
	Person p1(p0);//拷贝构造函数
	cout << "p0 年龄为： " << p0.age << endl;//显示为10
	cout << "p1 年龄为： " << p1.age << endl;//显示为10
	cout << endl;
```
 - **注意事项1**：**调用默认构造函数时，不要加小括号()**；因为下面这行代码，编译器会认为是函数的声明，不会认识是在创建对象，Person p1()

## 17.4 调用 — 显示法

```cpp
	//2.显示法
	Person p6;//默认构造
	Person p2 = Person(20);//有参构造
	Person p3 = Person(p2);//拷贝构造
	cout << "p2 年龄为： " << p2.age << endl;//显示为20
	cout << "p3 年龄为： " << p3.age << endl;//显示为20
	cout << endl;
```

 - **Person(10)**	匿名对象，特点：当前行执行结束后，系统会立即回收匿名对象
 - **注意事项2**：**不要利用拷贝函数初始化匿名对象**，编译器会认为Person (p3) == Person  p3;对象声明；Person(p3) —— 用拷贝函数初始化匿名对象
## 17.5 调用 — 隐式转换法

```cpp
	//3.隐式转换法
	Person p7;// 默认构造
	Person p4 = 30;//相当于	Person p4 = Person(10);有参构造 
	Person p5 = p4;//拷贝构造
	cout << "p4 年龄为： " << p4.age << endl;//显示为30
	cout << "p5 年龄为： " << p5.age << endl;//显示为30
	cout << endl;
```

 - 总的程序

```cpp
#include<iostream>
using namespace std;

//1.构造函数的分类及调用
//分类
//  按照参数分类   无参构造(默认构造)	有参构造
//  按照类型分类   普通构造		拷贝构造
class Person
{
public:
	//无参构造函数
	Person()
	{
		cout << "Person 无参构造函数的调用" << endl;
	}

	//有参构造函数
	Person(int a)
	{
		age = a;
		cout << "Person 有参构造函数的调用" << endl;
	}

	//拷贝构造函数
	Person(const Person& p)//拷贝一模一样的数据出来
	{
		//将传入的人身上所有属性，拷贝到我身上
		age = p.age;
	}

	//析构函数调用
	~Person()
	{
		cout << "Person 析构函数调用" << endl;
	}

	int age;
};

//调用(三种方法)
void test01()
{
	//1.括号法
	Person p;//默认构造函数调用
	Person p0(10);//有参构造函数
	Person p1(p0);//拷贝构造函数

	//注意事项1
	//调用默认构造函数时，不要加小括号()
	//因为下面这行代码，编译器会认为是函数的声明，不会认识是在创建对象
	//Person p1();

	cout << "p0 年龄为： " << p0.age << endl;//显示为10
	cout << "p1 年龄为： " << p1.age << endl;//显示为10
	cout << endl;

	//2.显示法
	Person p6;//默认构造
	Person p2 = Person(20);//有参构造
	Person p3 = Person(p2);//拷贝构造
	cout << "p2 年龄为： " << p2.age << endl;//显示为20
	cout << "p3 年龄为： " << p3.age << endl;//显示为20
	cout << endl;

	//Person(10);//匿名对象，特点：当前行执行结束后，系统会立即回收匿名对象
	// cout << "aaaaa" << endl;
	
	//注意事项2
	//不要利用拷贝函数初始化匿名对象，编译器会认为Person (p3) == Person  p3;对象声明
	//Person(p3);(会出错)

	//3.隐式转换法
	Person p7;// 默认构造
	Person p4 = 30;//相当于	Person p4 = Person(10);有参构造 
	Person p5 = p4;//拷贝构造
	cout << "p4 年龄为： " << p4.age << endl;//显示为30
	cout << "p5 年龄为： " << p5.age << endl;//显示为30
	cout << endl;
}

int main()
{
	test01();

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/1767f736ea624b35b8213d1b89caa08e.png)
 - 结论：**每次调用完函数，最后都会调用析构函数**

# 18 拷贝构造函数调用时机(3种情况)
C++中拷贝构造函数调用时机通常有三种情况

## 18.1 使用已经创建完毕的对象来初始化一个新对象

```cpp
//1.使用一个已经创建完毕的对象来初始化一个新对象
void test01()
{
	Person p1(20);// 有参构造
	Person p2(p1);// 拷贝构造

	cout << "p2 年龄为：" << p2.m_age << endl;// 20
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/01c38dd56bd04ffb8b4ee295582ef8cd.png)	
## 18.2 值传递的方式给函数参数传值

```cpp
//2.值传递的方式给函数参数传值
void doWork(Person p)// 值传递拷贝出临时的副本，不会影响下面的数据
{
}

void test02()
{
	Person p3;// 默认构造
	doWork(p3);// 实参调用形参时会调用拷贝构造函数
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/793a2e2c09f34d5a948fc1a5482b96d4.png)	

## 3.3 以值方式返回局部对象(难点)

```cpp
//3.值方式返回局部对象，局部对象 函数执行完之后，就会被释放掉
Person doWork2()
{
	Person p1;// 局部对象，默认构造，通过拷贝p1这个新的对象给外面
	cout << (int*)&p1 << endl;
	return p1;// p1是Person类型，通过第1行p1拷贝一个新的对象，返回给test03，拷贝构造
}

void test03()
{
	Person p = doWork2();// 创建局部对象
	cout << (int*)&p << endl;//p 和 p1不是一个
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/f18e468188054548a7828db7eb1e9d9a.png)

```cpp
#include<iostream>
using namespace std;

//拷贝构造函数调用的时机

class Person
{
public:
	Person()//无参构造函数
	{
		cout << "Person 默认构造函数调用" << endl;
	}

	Person(int age)//有参构造函数
	{
		cout << "Person 有参构造函数调用" << endl;
		m_age = age;
	}

	Person(const Person& p)//拷贝构造函数
	{
		cout << "Person 拷贝构造函数调用" << endl;
		m_age = p.m_age;
	}

	~Person()//析构函数
	{
		cout << "Person 析构函数调用" << endl;
	}

	int m_age;
};


//1.使用一个已经创建完毕的对象来初始化一个新对象
void test01()
{
	Person p1(20);// 有参构造
	Person p2(p1);// 拷贝构造

	cout << "p2 年龄为：" << p2.m_age << endl;// 20
}

//2.值传递的方式给函数参数传值
void doWork(Person p)// 值传递拷贝出临时的副本，不会影响下面的数据
{

}

void test02()
{
	Person p3;// 默认构造(无参)
	doWork(p3);// 实参调用形参时会调用拷贝构造函数，拷贝构造
}


//3.值方式返回局部对象，局部对象 函数执行完之后，就会被释放掉
Person doWork2()
{
	Person p1;// 局部对象，默认构造，通过拷贝p1这个新的对象给外面
	cout << (int*)&p1 << endl;
	return p1;// p1是Person类型，通过第1行p1拷贝一个新的对象，返回给test03，拷贝构造
}

void test03()
{
	Person p = doWork2();// 创建局部对象
	cout << (int*)&p << endl;//p 和 p1不是一个
}

int main()
{
	test01();
	cout << endl;
	test02();
	cout << endl;
	test03();

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/1ff4f8ff5fb742aba1e88f29a9021633.png)

# 19 构造函数调用规则
默认情况下，c++编译器至少给一个类添加3个函数

1. **默认构造函数**(无参，函数体为空)

2. **默认析构函数**(无参，函数体为空)

3. **默认拷贝构造函数，对属性进行值拷贝**

**构造函数调用规则**如下

* 如果用户**定义有参构造函数**，c++不再提供默认无参构造，但是会**提供默认拷贝构造**
* 如果用户**定义拷贝构造函数**，c++不会再提供其他构造函数
* **如果代码提供有参构造，编译器就不提供无参构造**
* **如果代码提供拷贝构造，编译器就不提供有参、无参构造**

```cpp
#include<iostream>
using namespace std;

//构造函数的调用规则
//1. 创建一个类，C++编译器会给每个类都添加至少3个函数
//默认构造 (空实现)
//析构函数 (空实现)
//拷贝函数 (值拷贝)

//2. 如果我们写了有参构造函数，编译器就不再提供默认构造，依然提供拷贝构造
//3. 如果我们写了拷贝构造函数，编译器就不再提供其他普通构造函数

class Person
{
public:
	//无参（默认）构造函数
	Person()
	{
		cout << "Person 默认构造函数调用" << endl;
	}
	//有参构造函数
	Person(int age)
	{
		m_age = age;
		cout << "Person 有参构造函数调用" << endl;
	}
	//拷贝构造函数
	Person(const Person& p)
	{
		m_age = p.m_age;
		cout << "Person 拷贝构造函数调用" << endl;
	}
	//析构函数
	~Person() {
		cout << "Person 析构函数调用" << endl;
	}

public:
	int m_age;
};

void test01()//test01执行完之后，p1和p2就被释放掉，执行它们的析构函数
{
	Person p1;//默认构造函数调用
	p1.m_age = 18;
	cout << "p1 年龄为: " << p1.m_age << endl;
	Person p2(p1);//拷贝构造函数调用
	cout << "p2 年龄为: " << p2.m_age << endl;
}

void test02()
{
	Person p;
}

int main()
{
	test01();
	cout << endl;

	test02();

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/398aeb126aca426e94f6dce77e6e2c0d.png)	
# 20 深拷贝和浅拷贝(难点)
深浅拷贝是面试经典问题，也是常见的一个坑

 - 浅拷贝：简单的赋值拷贝操作，如果利用编译器提供的拷贝构造函数，会做浅拷贝操作。就是程**序提供的等号赋值工作**
 - **直接使用 Person p2(p1) 使用编译器的浅拷贝**
 - 只有有参构造和无参构造的话，编译器会执行
 - **浅拷贝带来的问题是：堆区的内存重复释放**
 - 深拷贝：在堆区重新申请空间，进行拷贝操作
 - 深拷贝指针指向的堆区是不同的，在做释放时就不会出现错误。
![在这里插入图片描述](https://img-blog.csdnimg.cn/645856c501924b7887a0fb42b18e2cd5.png)
 - 栈的规则是先进后出，所以先释放p2，再释放p1，释放p2时已经释放堆区数据，释放p1时又在同一个堆区释放数据，造成数据释放重复

程序

 - **自己设置拷贝构造函数**


```cpp
	// 自己实现拷贝构造函数，解决浅拷贝带来的问题 
	Person(const Person& p)
	{
		cout << "Person 拷贝构造函数调用 " << endl;

		// 如果不利用深拷贝在堆区创建新内存，会导致浅拷贝带来的重复释放堆区问题
		m_age = p.m_age;
		// m_height = p.m_height;这是浅拷贝，编译器默认实现就是这行代码
		// 深拷贝操作 —— 重新在堆区创建一块内存
		m_height = new int(*p.m_height);// 解引用重新在堆区申请一块内存

	}
```

 - **析构函数**

```cpp
	// 析构函数 —— 作用是释放干净堆区的代码
	~Person()
	{
		// 析构代码，将堆区开辟的数据做释放操作
		cout << "析构函数调用" << endl;
		if (m_height != NULL)
		{
			delete m_height;// 利用delete释放干净
			m_height = NULL;// 防止野指针出现，置空操作
		}
	}
```


 - 总结：**如果属性有在堆区开辟的，一定要自己提供拷贝构造函数，防止浅拷贝带来的问题**

```cpp
#include<iostream>
using namespace std;

// 深拷贝和浅拷贝
// 浅拷贝：简单的赋值拷贝操作
// 深拷贝：在堆区重新申请空间，进行拷贝操作
class Person
{
public:
	// 无参构造函数(默认)
	Person()
	{
		cout << "Person 无参构造函数调用" << endl;
	}
	// 有参构造函数
	Person(int age, int height)
	{
		cout << "Person 有参构造函数调用" << endl;

		m_age = age;
		m_height = new int(height);
		// 利用new把身高创建在堆区，用指针接收堆区的数据
		// 堆区数据由程序员手动开辟和释放
	}

	// 自己实现拷贝构造函数，解决浅拷贝带来的问题 
	Person(const Person& p)
	{
		cout << "Person 拷贝构造函数调用 " << endl;

		// 如果不利用深拷贝在堆区创建新内存，会导致浅拷贝带来的重复释放堆区问题
		m_age = p.m_age;
		// m_height = p.m_height;这是浅拷贝，编译器默认实现就是这行代码
		// 深拷贝操作 —— 重新在堆区创建一块内存
		m_height = new int(*p.m_height);// 解引用重新在堆区申请一块内存

	}

	// 析构函数 —— 作用是释放干净堆区的代码
	~Person()
	{
		// 析构代码，将堆区开辟的数据做释放操作
		cout << "析构函数调用" << endl;
		if (m_height != NULL)
		{
			delete m_height;// 利用delete释放干净
			m_height = NULL;// 防止野指针出现，置空操作
		}
	}

	int m_age;// 年龄
	int* m_height;// 身高用指针，目的是把身高的数据开辟到堆区
};

void test01()// 栈的规则是先进后出，所以先释放p2，再释放p1
{
	// test01()执行完了，就可以释放p2，p1，销毁堆区数据
	Person p1(18, 180);// 有参构造函数，* 解引用解出数据

	cout << "p1 年龄： " << p1.m_age << " 身高： " << *p1.m_height << endl;

	Person p2(p1);// 深拷贝，如果利用编译器提供的拷贝构造函数，会做浅拷贝操作

	cout << "p2 年龄： " << p2.m_age << " 身高： " << *p2.m_height << endl;
}
// 浅拷贝的问题是堆区的内存被重复释放，先被p1释放，再被p2释放
// 浅拷贝问题用深拷贝解决

int main()
{
	test01();

	system("pause");
	return 0;
}
// 如果属性有在堆区开辟的，一定要自己提供拷贝构造函数，防止浅拷贝带来的问题
```
# 21 初始化列表

 - **作用：** C++提供了初始化列表语法，用来初始化属性
   **语法：**`构造函数()：属性1(值1),属性2（值2）... {}`

传统方式**利用构造函数初始化代码**

```cpp
#include<iostream>
using namespace std;

// 初始化列表
class Person {
public:

	// 传统方式初始化 利用构造函数初始化
	Person(int a, int b, int c) {
	m_A = a;
	m_B = b;
	m_C = c;
	}
	
	int m_A;
	int m_B;
	int m_C;
};

void test01()
{
	Person p(10, 20, 30);
	cout << "m_A: " << m_A << endl;
	cout << "m_B: " << m_B << endl;
	cout << "m_C: " << m_C << endl;
}

int main() {
	test01();
	system("pause");
	return 0;
}
```
**用初始化列表初始化属性**

```cpp
#include<iostream>
using namespace std;

// 初始化列表
class Person {
public:

	// 传统方式初始化 利用构造函数初始化
	//Person(int a, int b, int c) {
	//	m_A = a;
	//	m_B = b;
	//	m_C = c;
	//}

	//初始化列表方式初始化
	Person(int a, int b, int c) :m_A(a), m_B(b), m_C(c) {}
	void PrintPerson() {
		cout << "m_A = " << m_A << endl;
		cout << "m_B = " << m_B << endl;
		cout << "m_C = " << m_C << endl;
	}

private:
	int m_A;
	int m_B;
	int m_C;
};

int main() {

	Person p(1, 2, 3);
	p.PrintPerson();

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/65c64618742f49fcb9d12d0dc69e7f5e.png)	
# 22 类对象作为类成员
C++类中的成员可以是另一个类的对象，我们称该成员为 对象成员
例如：

```cpp
class A {}
class B
{
    A a；
}
```
B类中有对象A作为成员，A为对象成员

 - 当类中成员是其他类对象时，我们称该成员为 对象成员
 - 构造的顺序是 ：先调用对象成员的构造，再调用本类构造
 - 析构顺序与构造相反

```cpp
#include<iostream>
#include<string>// string 头文件
using namespace std;

// 类对象作为类成员 —— 对象成员

// 手机类 —— 人这个类的成员
class Phone
{
public:
	// 有参构造函数
	Phone(string pName)
	{
		cout << "Phone 有参构造函数调用" << endl;
		m_PName = pName;
	}

	~Phone()
	{
		cout << "Phone 析构函数调用" << endl;
	}

	// 手机品牌名称
	string m_PName;
};

// 人类
class Person
{
public:

	// Phone m_Phone = pName 隐式转换法，利用字符串给对象赋值
	// 初始化列表，相当于写了 Phone m_Phone = pName
	Person(string name, string pName) :m_Name(name), m_Phone(pName)
	{
		cout << "Person 构造函数调用" << endl;
	}

	~Person()
	{
		cout << "Person 析构函数调用" << endl;
	}

	// 姓名
	string m_Name;
	// 手机
	Phone m_Phone;// 设计手机类,phone是对象类型
};

// 当其他类对象作为本类成员，构造时先构造其他类对象（先phone再person），再构造自身。析构的顺序与构造相反

// 当类中成员是其他类对象时，我们称该成员为 对象成员
// 构造的顺序是 ：先调用对象成员的构造，再调用本类构造
// 析构顺序与构造相反

void test01()
{
	Person p("张三", "苹果MAX");

	cout << p.m_Name << "拿着" << p.m_Phone.m_PName << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
# 23 静态成员(成员变量和函数加static，重点难点)
静态成员就是在**成员变量和成员函数前加上关键字static**，称为**静态成员**
静态成员分为：
*  **静态成员变量**
   *  **所有对象共享同一份数据**
   *  在编译阶段分配内存(分配到全局区)
   *  类内声明，类外初始化
   *  **静态成员变量 —— 必须在类内声明，在类外初始化**
   * 静态成员变量也是有访问权限的,私有不可访问
   
*  **静态成员函数**
   *  所有对象共享同一个函数
   *  **静态成员函数只能访问静态成员变量**

* **静态成员变量访问方式**
	* 通过对象进行访问
	* 通过类名进行访问

## 23.1 静态成员变量

```cpp
#include<iostream>
using namespace std;

class Person
{
public:

	static int m_A; // 静态成员变量

	// 静态成员变量特点：
	// 1 在编译阶段分配内存(全局区)
	// 2 类内声明，类外初始化
	// 3 所有对象共享同一份数据

private:
	static int m_B; // 静态成员变量也是有访问权限的
};

int Person::m_A = 100;// Person下的静态变量类外声明
int Person::m_B = 300;

void test01()
{
	Person p;
	cout << p.m_A << endl;// 100

	Person p2;
	p2.m_A = 200;

	cout << p.m_A << endl;// 200 因为所有对象共享同一份数据 
}

void test02()
{
	// 静态成员变量两种访问方式

	// 1、通过对象进行访问
	Person p1;
	p1.m_A = 100;
	cout << "p1.m_A = " << p1.m_A << endl;

	Person p2;
	p2.m_A = 200;
	cout << "p1.m_A = " << p1.m_A << endl; // 共享同一份数据
	cout << "p2.m_A = " << p2.m_A << endl;

	// 2、通过类名
	cout << "m_A = " << Person::m_A << endl;

	//cout << "m_B = " << Person::m_B << endl; // 私有权限访问不到
}

int main() {

	test01();

	system("pause");
	return 0;
}
```
## 23.2 静态成员函数

```cpp
#include<iostream>
using namespace std;

// 静态成员函数特点
// 1 所有对象共享同一个函数
// 2 静态成员函数只能访问静态成员变量
class Person
{
public:
	// 静态成员函数
	static void func()
	{
		m_A = 100;// 静态成员函数可以访问 静态成员变量(共享)
		//m_B = 200;// 静态成员函数 不可以访问 非静态成员变量，无法区分到底是哪个对象的m_B的属性
		cout << "static void func 调用" << endl;
	}

	// 静态成员变量特点
	// 1 在编译阶段分配内存
	// 2 类内声明，类外初始化
	// 3 所有对象共享同一份数据
	// 静态成员变量 —— 必须在类内声明，在类外初始化
	static int m_A; // 静态成员变量
	int m_B;// 非静态成员变量

	// 静态成员函数也是有访问权限的,私有不可访问
private:
	static void func2()
	{
		cout << "static void func2 调用" << endl;
	}
};

int Person::m_A = 10;// 静态成员变量类外的初始化
// int Person::m_B = 10; 

void test01()
{
	// 静态成员函数两种访问方式
	// 1. 通过对象进行访问
	Person p;
	p.func();

	// 2. 通过类名进行访问
	Person::func();
	// Person::func2();//类外访问不到私有的静态成员函数
}

int main()
{
	test01();

	system("pause");
	return 0;
}
```

# 核心4 类和对象\_C++对象模型、this指针、友元

# 24 C++对象模型和this指针(重难点)
## 24.1 成员变量和成员函数分开存储
 - C++中，类内的成员变量和成员函数分开存储，**只有非静态成员变量才属于类的对象上，其他都是独一份**

### 24.1.1 空对象

 - C++编译器会**给每个空对象也分配一个字节空间**，是为**区分空对象占内存的位置**
 - **每个空对象也应该有个独一无二的内存地址**
 - 空对象占用的内存空间为: 1字节

```cpp
#include<iostream>
using namespace std;

// 成员变量 和 成员函数 分开存储
// 只有非静态成员变量才属于类的对象上，其他都是独一份

// 空对象
class Person
{
};

void test01()
{
	// C++编译器会给每个空对象也分配一个字节空间，是为了区分空对象占内存的位置
	// 每个空对象也应该有个独一无二的内存地址
	Person p;
	// 空对象占用的内存空间为: 1
	cout << "size of p=" << sizeof(p) << endl;
}

int main()
{
	test01();//1个字节

	system("pause");
	return 0;
}
```
### 24.1.2 非空对象
 - **非静态成员变量，属于类的对象上** 
 - 静态成员变量：**需要类内声明，类外初始化，不属于类的对象上** 
 - 非静态成员函数，不属于类的对象上
 - 静态成员函数，不属于类的对象上

```cpp
#include<iostream>
using namespace std;

// 成员变量 和 成员函数 分开存储
// 只有非静态成员变量才属于类的对象上，其他都是独一份

class Person
{
	int m_A;// 非静态成员变量，属于类的对象上

	static int m_B;// 静态成员变量 —— 需要类内声明，类外初始化，不属于类的对象上

	void func() {} // 非静态成员函数，不属于类的对象上

	static void func2() {}// 静态成员函数，不属于类的对象上
};

int Person::m_B = 10;

void test01() // 空对象，class里面没有内容
{
	// C++编译器会给每个空对象也分配一个字节空间，是为了区分空对象占内存的位置
	// 每个空对象也应该有个独一无二的内存地址
	Person p;
	// 空对象占用的内存空间为: 1
	cout << "size of p = " << sizeof(p) << endl;
}

void test02()
{
	Person p1;// 此时不是空对象
	cout << "size of p1 =" << sizeof(p1) << endl;// 4个字节
}

int main()
{
	test01();//1个字节
	test02();//4个字节

	system("pause");
	return 0;
}
```
## 24.2 this指针(指向被调用的成员函数所属的对象)
通过上面我们知道在C++中成员变量和成员函数是分开存储的，**每一个非静态成员函数只会诞生一份函数实例**，就是说**多个同类型的对象会共用一块代码**

> **问题是：这一块代码是如何区分那个对象调用自己的呢？就是说假设只有一个函数，有很多的对象p1,p2,p3都在使用这个函数,在函数体内部如何区分是p1调的还是p2调的，修改属性**

 - C++通过提供特殊的对象指针，this指针，解决上述问题。**this指针指向被调用的成员函数所属的对象，就是p1调用成员函数，this就指向p1；p2调用成员函数，this就指向p2，以此类推，哪个对象调用成员函数，则this指向哪个对象。**
 - **this指针是隐含每一个非静态成员函数内的一种指针**，this指针不需要定义，**直接使用即可**

> **this指针的用途**：

 *  **当形参和成员变量同名时，可用this指针来区分**
 *  在类的非静态成员函数中返回对象本身，可使用return *this

>  **this指针的本质 是指针常量 指针的指向是不可以修改的**

### 24.2.1 解决冲突问题
>  方法1：使用m_，区分和形参的名称

```cpp
public:
	Person(int age)//这是形参age
	{
		m_age = age; // 成员member,后面需要
	}
	int m_age;
```

>  方法2：使用this指针(推荐)

 * p1 在**调用有参构造函数，所以this指向被调用的成员函数所属的对象**

```cpp
public:
	Person(int age)//这是形参age
	{
		//this指针指向 被调用成员函数 所属的对象
		//this指的是成员属性age，后面是形参age
		this->age = age;
	}
	int age;
```

### 24.2.2 返回对象本身用*this
```cpp
Person& PersonAddAge2(Person &p)// 第2个Person&表示以引用的方式传入
	{
		this->age += p.age;// 将别人的年龄加到自身上面

		// this指向p2的指针，*this指向的就是p2这个对象的本体
		return *this;// 要返回本体，要用引用的方式返回，不能只用值返回Person
	}
```

### 24.2.3 Person&使用(重难点)

 - 如果开头Person&变成Person的话，会变成值传递，Person就会创建和本体不一样的新数据，调用拷贝构造函数(用值得方式返回，会复制一份新的数据，Person和*this自身是不一样的数据)。通过一次次链式传递，新生成不同于p2的新的对象，每次返回的都是新的对象。
 - 使用Person的话，就是拷贝调用新的数据，作为返回值
 - 下面的写法不能使用

```cpp
Person PersonAddAge2(Person &p)// 第2个Person&表示以引用的方式传入
	{
		this->age += p.age;// 将别人的年龄加到自身上面

		// this指向p2的指针，*this指向的就是p2这个对象的本体
		return *this;// 要返回本体，要用引用的方式返回，不能只用值返回Person
		// 如果开头Person&变成Person的话，就会变成值传递
	}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/8232fd6fb31747a68f793d4e1e2172ed.png)
## 24.3 空指针访问成员函数
 - C++中空指针也是可以调用成员函数的，但是也要注意有没有用到this指针，成员函数
 - 如果用到this指针，需要加以判断保证代码的健壮性，使用下面程序

```cpp
if (this == NULL)
{
    return;
}
```
 - **属性的前面都默认加入了this指针，this是个空值，没有确定的对象，也就不能访问属性m_age，不然就是无中生有，会报错**
```cpp
#include<iostream>
using namespace std;

//空指针调用成员函数

class Person
{
public:

	void showClassName()
	{
		cout << "this is Person class" << endl;
	}

	void showPersonName()
	{
		// 报错的原因是传入的指针为空NULL，没法无中生有
		if (this == NULL)
		{
			return;
		}
		// 属性的前面都默认加入了this指针，this是个空值，没有确定的对象
		cout << "age = " << this->m_Age << endl;// 属性默认加this
	}

	int m_Age;
};

void test01()
{
	Person* p = NULL;
	p->showClassName();
	p->showPersonName();

	Person p1;
	p1.showClassName();
	p1.showPersonName();
}

int main()
{
	test01();

	system("pause");
	return 0;
}
```
## 24.4 const 修饰成员函数(常函数 常对象)
**this指针** —— 指针常量，不加const指向的值可以修改
 * this指针的本质是**指针常量**，指针的指向是不可以修改的，不加const指向的值可以修改
 * this指针不可以修改指针的指向，若要指针指向的值也不可以修改，函数后面加const
 * const Person * const this：**前面const限制指针的值不可以修改，后面const限制指针的指向不可以修改**
 *  成员函数后面加const，修饰的是this指针，让指针指向的值也不可以修改

### 24.4.1 常函数

* **成员函数后加const**后我们称为这个函数为**常函数**
* **常函数内不可以修改成员属性**
* **成员属性声明时加关键字mutable后，在常函数和常对象中依然可以修改**

```cpp
// 常函数 —— 成员函数后加const，常函数内不可以修改成员属性
class Person
{
public:
	// this指针的本质 是指针常量 指针的指向是不可以修改的

	// const Person * const this
// 前面const限制指针的值不可以修改，后面const限制指针的指向不可以修改

// 在成员函数后面加const，修饰的是this指针，让指针指向的值也不可以修改
	void showPerson() const		//加入const后，属性值就不可以修改
	{
		this->m_B = 100;
		// this->m_A = 100;
		// this = NULL;
		//this指针不可以修改指针的指向，若要指针指向的值也不可以修改，函数后面加const
	}

	//普通函数
	void func() {}

	int m_A;
	//特殊变量，即使在常函数和常对象中，也可以修改这个值。加上关键字mutable，m_B可以修改值
	mutable int m_B;
};
```
### 24.4.2 常对象
**常对象：**
 * **声明对象前加const**称该对象为常对象
 * **常对象只能调用常函数，不可以调用普通的成员函数，因为普通成员函数可以修改属性**

```cpp
void test02()
{
	const Person p;// 在对象前加const，变为常对象
	// p.m_A = 100;// 对象属性不可以修改(报错)
	p.m_B = 100;// m_B是特殊值，在常对象下也可以修改(加上mutable)

	// 常对象只能调用常函数
	p.showPerson();
	// p.func();// 常对象不可以调用普通的成员函数，因为普通成员函数可以修改属性
}
```
总程序

```cpp
#include<iostream>
using namespace std;

// 常函数 —— 成员函数后加const，常函数内不可以修改成员属性
class Person
{
public:
	// this指针的本质 是指针常量 指针的指向是不可以修改的

	// const Person * const this
	// 前面const限制指针的值不可以修改，后面const限制指针的指向不可以修改

	// 在成员函数后面加const，修饰的是this指针，让指针指向的值也不可以修改
	void showPerson() const		//加入const后，属性值就不可以修改
	{
		this->m_B = 100;
		// this->m_A = 100;
		// this = NULL;
		//this指针不可以修改指针的指向，若要指针指向的值也不可以修改，函数后面加const
	}

	//普通函数
	void func() {}

	int m_A;
	//特殊变量，即使在常函数和常对象中，也可以修改这个值。加上关键字mutable，m_B可以修改值
	mutable int m_B;
};

void test01()
{
	Person p;
	p.showPerson();
}

//常对象
void test02()
{
	const Person p;// 在对象前加const，变为常对象
	// p.m_A = 100;// 对象属性不可以修改(报错)
	p.m_B = 100;// m_B是特殊值，在常对象下也可以修改(加上mutable)

	// 常对象只能调用常函数
	p.showPerson();
	// p.func();// 常对象不可以调用普通的成员函数，因为普通成员函数可以修改属性
}

int main()
{
	system("pause");
	return 0;
}
```
# 25 友元(便于访问私有函数)
- 生活中你的家有客厅(Public)，有你的卧室(Private)，客厅所有来的客人都可以进去，但是你的卧室是私有的，也就是说只有你能进去，但是你也可以允许你的好闺蜜好基友进去
- 在程序里，有些私有属性，**想让类外特殊的一些函数或者类进行访问，就需要用到友元的技术**，**友元的目的就是让一个函数或者类访问另一个类中私有成员**，友元的关键字为**friend**

## 25.1 全局函数做友元
```cpp
#include<iostream>
#include<string>
using namespace std;

// 建筑物类
class Building
{
	// goodgay全局函数 是 Building好朋友，可以访问 Building 找那个私有成员
	friend void goodGay(Building* building);

public:
	// 无参构造函数
	Building()
	{
		// 赋初值
		m_SittingRoom = "客厅";
		m_BedRoom = "卧室";
	}

public:
	string m_SittingRoom;// 客厅

private:
	string m_BedRoom;// 卧室
};

// 全局函数 - 好朋友 访问私有成员
void goodGay(Building* building) // 传入指针Building(引用也可以)
{
	cout << "好基友的全局函数 正在访问：" << building->m_SittingRoom << endl;// 公共属性

	cout << "好基友的全局函数 正在访问：" << building->m_BedRoom << endl;// 私有属性
}

void test01()
{
	Building building1;// 实例化Building对象
	goodGay(&building1);// 以指针的形式(传入地址)将对象传入全局函数
}

int main()
{
	test01();

	system("pause");
	return 0;
}
```
## 25.2 类做友元：一个类可以访问另一个类的私有成员(难点)

 - 类外构建成员函数


```cpp
class Building
{
public:
	// 无参构造函数
	Building();

public:
	string m_SittingRoom;// 客厅

private:
	string m_BedRoom;// 卧室
};

// 类外写成员函数
Building::Building() // 类中的成员函数，Building下面的构造函数Building
{
	m_SittingRoom = "客厅";
	m_BedRoom = "卧室";
}
```
步骤：
1. 创建goodGay对象，调用goodGay的构造函数
2. 首先调用 类GoodGay 无参构造函数GoodGay()——成员函数 GoodGay::GoodGay()，使用new Builing 创建一个building对象
3. 在创建该对象的同时还调用Building构造函数——Building::Building()，里面已经赋好初值了。
4. 调用visit函数，可以访问building内部维护的m_settingRoom
5. **friend class goodGay：可以让goodGay访问Building里面的私有成员**

```cpp
#include<iostream>
#include<string>
using namespace std;

// 类做友元：让一个类可以访问另一个类的私有成员

class Building;// 创建building,告诉编译器一会会写这个类

class GoodGay// 创建goodgay类
{
public:
	// 无参构造函数
	GoodGay();
	// 参观函数  访问Building中的属性 公共和私有属性
	void visit();

private:
	Building* building;// 指针类型
};

class Building
{
	// GoodGay类是本类的好朋友，可以访问本类Building的私有成员
	friend class GoodGay;

public: 
    // 赋初值
	// 无参构造函数
	Building();

public:
	string m_SittingRoom;// 客厅

private:
	string m_BedRoom;// 卧室
};

// 类外写成员函数
Building::Building() // 类中的成员函数，Building下面的构造函数Building，赋初值
{
	m_SittingRoom = "客厅";
	m_BedRoom = "卧室";
}

GoodGay::GoodGay()
{
	// 创建建筑物对象
	building = new Building;
	// new表示在堆区创建出一个对象,new什么样的类型，就返回什么样的指针
}

void GoodGay::visit()// goodgay下面的函数
{
	cout << "好基友类正在访问：" << building->m_SittingRoom << endl;

	cout << "好基友类正在访问：" << building->m_BedRoom << endl;
}

void test01()
{
	GoodGay gg;// 创建goodGay对象，调用goodGay的构造函数
	gg.visit();
}

int main()
{
	test01();

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/6cfa95d6eaab41bbbcd88a985478242a.png)	
## 25.3 成员函数做友元
```cpp
building1 = new Building;
	// building指针等于new的Building对象
	// 相当于在堆区创建一个Building对象，并且用指针维护这个建筑物对象
```

```cpp
// 告诉编译器，GoodGay类下的visit1成员函数作为本类的好朋友，可以访问私有成员
	friend void GoodGay::visit1();
	// friend void GoodGay::visit2();// 没有这句的话visit2不可以访问私有成员，只能访问私有属性
```

```cpp
#include<iostream>
#include<string>
using namespace std;

class Building;// 首先声明Building类
class GoodGay
{
public:
	// 无参构造函数
	GoodGay();

	// 用类外实现函数
	void visit1();// 让visit函数可以访问Building中私有成员
	void visit2();// 让visit2函数不可以访问Building中私有成员

	Building* building1;
};

class Building
{
	// 告诉编译器，GoodGay类下的visit1成员函数作为本类的好朋友，可以访问私有成员
	friend void GoodGay::visit1();
	// friend void GoodGay::visit2();// 没有这句的话visit2不可以访问私有成员

public:
	Building();// 构造函数的声明

public:
	string m_SittingRoom;// 客厅

private:
	string m_BedRoom;// 客厅
};

// 类外实现成员函数
Building::Building()
{
	m_SittingRoom = "客厅";
	m_BedRoom = "卧室";
}

GoodGay::GoodGay()// 类外实现
{
	building1 = new Building;
	// building指针等于new的Building对象
	// 相当于在堆区创建一个Building对象，并且用指针维护这个建筑物对象
}

void GoodGay::visit1()
{
	cout << "visit1 函数正在访问：" << building1->m_SittingRoom << endl;

	cout << "visit1 函数正在访问：" << building1->m_BedRoom << endl;
}

void GoodGay::visit2()
{
	cout << "visit2 函数正在访问：" << building1->m_SittingRoom << endl;

	// cout << "visit2函数正在访问：" << building1->m_BedRoom << endl;
	// 成员函数不做友元，不能访问私有成员
}

void test01()
{
	GoodGay gg;
	gg.visit1();
	gg.visit2();
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/50c956a38dca411482ef130208d05e02.png)	

# 核心5 类和对象_运算符重载(难点)

- 运算符重载概念：**对已有的运算符重新进行定义，赋予其另一种功能，以适应不同的数据类型**

# 26 运算符重载(成员函数或全局函数重载)
## 26.1 加号运算符重载
![在这里插入图片描述](https://img-blog.csdnimg.cn/5f27953a99e143e8ac7ca05ac616b0a5.png)
上述是无法实现相加

 - 通过自己写两个成员函数，实现两个对象相加属性后返回新的对象
 - 自身对象的A属性 + 传进来的对象的A属性 再赋值给新的对象
![在这里插入图片描述](https://img-blog.csdnimg.cn/c5f55beb6e094a2a974e9b5b982f4277.png)
 - 编译器给取了一个通用名称

- **同过成员函数重载+号**

![在这里插入图片描述](https://img-blog.csdnimg.cn/ecc3d856b7b745039a2e18d6ca3665b4.png)

 - **通过全局函数重载+**
    ![在这里插入图片描述](https://img-blog.csdnimg.cn/daac4bb82e184d6fb80cf4f2b84a52e2.png)
 - 结果

![在这里插入图片描述](https://img-blog.csdnimg.cn/952a81ceca6b4dae85c1831e10c00bf2.png)
### 26.1.1 成员函数重载 +

```cpp
class Person
{
public:
	// 方式1、成员函数重载+号, this指的是正在调用的对象
	Person operator+(Person& p)
	{
		Person temp;
		temp.m_A = this->m_A + p.m_A;
		temp.m_B = this->m_B + p.m_B;
		return temp;
	}

	int m_A;
	int m_B;
};

// 成员函数重载本质调用，这里this指向的就是p1
Person p2 = p0.operator+(p1);
```
### 26.1.2 全局函数重载 +
```cpp
// 方式2、全局函数重载+号
Person operator+(Person& p1, Person& p2)
{
	Person temp;
	temp.m_A = p1.m_A + p2.m_A;
	temp.m_B = p1.m_B + p2.m_B;
	return temp;
}

// 全局函数重载本质调用
Person p3 = operator+(p1, p2);
//Person p3 = p0 + p1;// 全局函数重载和成员函数重载均可以使用这种方式
```
### 26.1.3 函数重载 +(重点)
函数重载满足条件：

 - 同一个作用域(比如都是成员函数)
 - 函数名一样operator
 - 参数不一样，个数，类型，顺序不一样
 - 返回值不作为重载条件

```cpp
// 函数重载+
Person operator+(Person& p1, int num)
{
	Person temp;
	temp.m_A = p1.m_A + num;
	temp.m_B = p1.m_B + num;
	return temp;
}

// 运算符重载也可以发生函数重载
Person p4 = p0 + 100;//Person + int
```

```cpp
#include<iostream>
using namespace std;
// 加号运算符重载
class Person
{
public:
	// 方式1、成员函数重载+号, this指的是正在调用的对象
	Person operator+(Person& p)
	{
		Person temp;
		temp.m_A = this->m_A + p.m_A;
		temp.m_B = this->m_B + p.m_B;
		return temp;
	}

	int m_A;
	int m_B;
};

// 方式2、全局函数重载+号
Person operator+(Person& p1, Person& p2)
{
	Person temp;
	temp.m_A = p1.m_A + p2.m_A;
	temp.m_B = p1.m_B + p2.m_B;
	return temp;
}

// 函数重载+
Person operator+(Person& p1, int num)
{
	Person temp;
	temp.m_A = p1.m_A + num;
	temp.m_B = p1.m_B + num;
	return temp;
}

void test01()
{
	Person p0;
	p0.m_A = 10;
	p0.m_B = 10;
	Person p1;
	p1.m_A = 20;
	p1.m_B = 20;

	// 成员函数重载本质调用，这里this指向的就是p0
	Person p2 = p0.operator+(p1);
	cout << "p2.m_A = " << p2.m_A << endl;
	cout << "p2.m_B = " << p2.m_B << endl;

	// 全局函数重载本质调用
	Person p3 = operator+(p0, p1);
	//Person p3 = p0 + p1;// 全局函数重载和成员函数重载均可以使用这种方式
	cout << "p3.m_A = " << p3.m_A << endl;
	cout << "p3.m_B = " << p3.m_B << endl;

	// 运算符重载也可以发生函数重载
	Person p4 = p0 + 100;// Person + int
	cout << "p4.m_A = " << p4.m_A << endl;
	cout << "p4.m_B = " << p4.m_B << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/95d703ff48fd4ae8b9a08aa0a1011a51.png)	
> 总结1：对于内置的数据类型的表达式的的运算符是不可能改变的

> 总结2：不要滥用运算符重载

## 26.2 左移运算符重载(输出自定义数据类型)
 - 作用：**可以输出自定义数据类型**
 - p.operator<<(cout) 简化版本 p << cout，通常**不会用成员函数重载<<运算符**，因为无法实现 cout 在左侧
 - **只能利用全局函数重载左移运算符**
 - cout 是类ostream的对象，就是**标准输出流的对象**，且全局只能有一个，用**引用的方式传递**
 - 本质 operator << (cout,p) 简化cout << p; cout数据类型是ostream(输出流)

```cpp
#include<iostream>
using namespace std;

//左移运算符重载——可以输出自定义数据类型
//重载左移运算符配合友元可以实现输出自定义数据类型

class Person
{
	// 作为person类的好朋友，访问私有内容
	friend ostream& operator << (ostream& cout, Person& p);

public:
	Person(int a, int b)
	{
		m_A = a;
		m_B = b;
	}

private:

	// 左移运算符只有一个对象
	// 利用成员函数重载 左移运算符(不知道先返回什么，就写一个void) 
	// p.operator<<(cout) 简化版本 p << cout
	// 通常不会用成员函数重载<<运算符，因为无法实现 cout 在左侧
	/*void operator<<(Person& p)
	{
	}*/

	int m_A;
	int m_B;
};

// 只能利用全局函数重载左移运算符
// cout是类ostream的对象，就是标准输出流的对象，且全局只能有一个，用引用方式传递
// 本质 operator << (cout,p) 简化cout << p; cout数据类型是ostream(输出流)
ostream& operator << (ostream& cout, Person& p)
{
	cout << "m_A = " << p.m_A << " m_B = " << p.m_B << endl;
	return cout;// 解引用ostream，返回cout,可以无限往后追加输入
}

void test01()
{
	// 方式1
	// Person p;
	// p.m_A = 10;
	// p.m_B = 10;
	// cout << p.m_A << endl;
	// cout << p.m_B << endl;

	// 方式2
	Person p(10, 10);
	cout << p << "hello " << endl;// 可以输出p
}

int main()
{
	test01();

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/36d6f2d4ace54f518c4f516f6c83d07b.png)	
 - **总结：重载左移运算符配合友元可以实现输出自定义数据类型**

## 26.3 递增运算符重载(自己定义自增自减)

 - 作用： 通过重载递增运算符，实现自己的整型数据

![在这里插入图片描述](https://img-blog.csdnimg.cn/ae2eaef9e1b74dfe9330d31c69f008a8.png)

 - this指向自身，返回引用 *this
### 26.3.1 重载前置++运算符(返回是引用)
```cpp
	// 返回引用是为了一直对一个数据进行递增操作
	MyInteger& operator++()
	{
		// 先进行 ++ 运算
		m_Num++;

		// 再将自身做返回
		return *this;// this指向自身，返回引用
	}
```

### 26.3.2 重载后置++运算符(返回是值)-重点

 - 如果**加入返回的是引用**，由于**返回的是局部的对象的引用**，局部对象在当前函数(MyInteger temp = *this)执行完之后就会释放，继续返回引用(return temp)就是非法操作。

```cpp
	// 先记录当时的结果
	MyInteger temp = *this;//*this表示自身，记录自身结果
	// 后递增
	m_Num++;
	// 最后将记录结果做返回
	return temp;
```

```cpp
    // void operator++(int) int代表占位参数，可以区分前置和后置递增
	// MyInteger&表示返回局部对象的引用，temp是局部变量，返回局部对象的引用
	// 局部对象在当前函数结束后就被释放，继续返回引用为非法操作
	MyInteger operator++(int)// 返回值不可以作为重载的条件,返回的是值
	{
		// 先记录当时的结果
		MyInteger temp = *this;//*this表示自身，记录自身结果
		// 后递增
		m_Num++;
		// 最后将记录结果做返回
		return temp;
	}
```

```cpp
#include<iostream>
using namespace std;

//重载递增运算符

//自定义整型
class MyInteger
{
	friend ostream& operator<<(ostream& cout, MyInteger myint);

public:
	MyInteger()
	{
		m_Num = 0;
	}

	// 重载前置 ++ 运算符(返回的是引用)
	// 返回引用是为了一直对一个数据进行递增操作
	MyInteger& operator++()
	{
		// 先进行 ++ 运算
		m_Num++;

		// 再将自身做返回
		return *this;// this指向自身，返回引用
	}

	// 重载后置 ++ 运算符(返回的是值)
	// void operator++(int) int代表占位参数，可以区分前置和后置递增
	// MyInteger&表示返回局部对象的引用，temp是局部变量，返回局部对象的引用
	// 局部对象在当前函数结束后就被释放，继续返回引用为非法操作
	MyInteger operator++(int)// 返回值不可以作为重载的条件,返回的是值
	{
		// 先记录当时的结果
		MyInteger temp = *this;//*this表示自身，记录自身结果
		// 如果加入返回的是引用，由于返回的是局部的对象的引用，局部对象在当前函数执行完之后就会释放
		// 继续返回引用就是非法操作
		// 后递增
		m_Num++;
		// 最后将记录结果做返回
		return temp;
	}

private:
	int m_Num;
};

// 利用全局运算符重载左移运算符   重载 << 运算符
ostream& operator<<(ostream& cout, MyInteger myint)
{
	cout << myint.m_Num;// m_Num 私有化
	return cout;
}

void test01()
{
	MyInteger myint;

	cout << ++myint << endl;
}

void test02()
{
	MyInteger myint;

	cout << myint++ << endl;
}

int main()
{
	test01();
	test02();

	system("pause");
	return 0;
}
```
## 26.4 赋值运算符
C++编译器至少给一个类添加4个函数

1. 默认构造函数(无参，函数体为空)
2. 默认析构函数(无参，函数体为空)
3. 默认拷贝构造函数，对属性进行值拷贝
4. 赋值运算符 operator=, 对属性进行值拷贝

如果类中有属性指向堆区，做赋值操作时也会出现深浅拷贝问题

 - 编译系统提供的等号赋值操作，是**浅拷贝**，p2先执行右边的析构代码，先判断是否为空，不为空，释放堆区内存。p1再执行右边的析构代码，判断p1是否为空，也不为空，释放相同的堆区内存，导致堆区的内存重复释放，导致奔溃。
![在这里插入图片描述](https://img-blog.csdnimg.cn/04fdd8fe42264054961b00f12e34c384.png)
 - 解决方法：使用深拷贝，使p2和p1分别指向不同的堆区内存

![在这里插入图片描述](https://img-blog.csdnimg.cn/996bbd52989f4ea6b1f31aa42b9acfe1.png)

```cpp
#include<iostream>
using namespace std;

class Person
{
public:

	Person(int age)
	{
		// 将年龄数据开辟到堆区
		m_Age = new int(age);// new int 返回的是int*，
	}

	// 重载赋值运算符 
	Person& operator=(Person& p)
	{
		// 编译器提供的代码是浅拷贝
		// m_Age = p.m_Age;

		// 先判断是否有属性在堆区，如果有，先释放干净，然后再深拷贝
		if (m_Age != NULL)
		{
			delete m_Age;
			m_Age = NULL;
		}
		
		// 提供深拷贝 解决浅拷贝的问题
		m_Age = new int(*p.m_Age);// new一个int类型空间

		// 返回自身
		return *this;
	}

	// 析构函数 堆区的数据要手动释放 —— 有数字就释放
	~Person()
	{
		if (m_Age != NULL)
		{
			delete m_Age;
			m_Age = NULL;
		}
	}

	// 年龄的指针
	int* m_Age;
};


void test01()
{
	Person p1(18);
	Person p2(20);
	Person p3(30);

	p3 = p2 = p1; // 赋值操作

	cout << "p1的年龄为：" << *p1.m_Age << endl;
	cout << "p2的年龄为：" << *p2.m_Age << endl;
	cout << "p3的年龄为：" << *p3.m_Age << endl;
}

int main() {

	test01();
	system("pause");
	return 0;
}
```
## 26.5 关系运算符重载
 - **作用：**重载关系运算符，可以让两个自定义类型对象进行对比操作
### 26.5.1 重载 == 号

```cpp
bool operator==(Person& p)
	{
		if (this->m_Name == p.m_Name && this->m_Age == p.m_Age)
		{
			return true;
		}
		else
		{
			return false;
		}
	}
```
### 26.5.2 重载 != 号

```cpp
bool operator!=(Person& p)
{
    if (this->m_Name == p.m_Name && this->m_Age == p.m_Age)
    {
        return false;
    }
    else
    {
        return true;
    }
}
```

```cpp
#include<iostream>
using namespace std;

class Person
{
public:
	Person(string name, int age)
	{
		this->m_Name = name;
		this->m_Age = age;
	};

	// 重载 == 号
	bool operator==(Person& p)
	{
		if (this->m_Name == p.m_Name && this->m_Age == p.m_Age)
		{
			return true;
		}
		else
		{
			return false;
		}
	}

	// 重载 != 号
	bool operator!=(Person& p)
	{
		if (this->m_Name == p.m_Name && this->m_Age == p.m_Age)
		{
			return false;
		}
		else
		{
			return true;
		}
	}

	string m_Name;
	int m_Age;
};

void test01()
{
	//int a = 0;
	//int b = 0;

	Person a("孙悟空", 18);
	Person b("孙悟空", 18);

	if (a == b)
	{
		cout << "a 和 b 相等" << endl;
	}
	else
	{
		cout << "a 和 b 不相等" << endl;
	}

	Person c("孙悟空", 18);
	Person d("孙悟空", 20);

	if (c != d)
	{
		cout << "c 和 d 不相等" << endl;
	}
	else
	{
		cout << "c 和 d 相等" << endl;
	}
}

int main()
{
	test01();

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/472fad73e1e841e4bcdb1fdb1d6b6ecd.png)	
## 26.6 函数调用运算符重载(仿函数)
* **函数调用运算符 () 也可以重载**
* 由于重载后使用的方式非常像函数的调用，因此称为仿函数
* 仿函数没有固定写法，非常灵活

```cpp
#include<iostream>
using namespace std;
#include<string>

// 函数调用运算符重载

// 打印输出类
class MyPrint
{
public:
	void operator()(string text)// 重载()操作符
	{
		cout << text << endl;
	}
};

void MyPrint02(string test)
{
	cout << test << endl;
}

void test01()
{
	// 重载函数调用运算符
	MyPrint myFunc;
	// 由于使用起来非常类似于函数调用，因此称为仿函数
	myFunc("hello world");
	
	// 函数调用
	MyPrint02("hello!");
}

// 仿函数非常灵活，没有固定的手法
// 加法类
class MyAdd
{
public:
	int operator()(int v1, int v2)
	{
		return v1 + v2;
	}
};
void test02()
{
	MyAdd add;
	int ret = add(10, 10);
	cout << "ret = " << ret << endl;

	//匿名函数对象 —— 匿名对象 有重载小括号
	cout << "MyAdd()(100,100) = " << MyAdd()(100, 100) << endl;
}

int main() {

	test01();
	test02();

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/afccd0230f5d463fb7c5559ff6468e46.png)	

# 核心6 类和对象_继承(重难点)

# 27 继承

**继承是面向对象三大特性之一**

有些类与类之间存在特殊的关系，例如下图中：
![在这里插入图片描述](https://img-blog.csdnimg.cn/6158de437d7f40eb99d23f9df52d22d4.png)
我们发现，定义这些类时，下级别的成员除了拥有上一级的共性，还有自己的特性。

这个时候我们就可以考虑利用继承的技术，减少重复代码
## 27.1 继承基本语法
例如我们看到很多网站中，都有**公共的头部，公共的底部，甚至公共的左侧列表，只有中心内容不同**，接下来我们分别利用普通写法和继承的写法来实现网页中的内容，看一下继承存在的意义以及好处

### 27.1.1 普通实现(重复率高)

```cpp
//Java页面
class Java 
{
public:
	void header()
	{
		cout << "首页、公开课、登录、注册...（公共头部）" << endl;
	}
	void footer()
	{
		cout << "帮助中心、交流合作、站内地图...(公共底部)" << endl;
	}
	void left()
	{
		cout << "Java,Python,C++...(公共分类列表)" << endl;
	}
	void content()
	{
		cout << "JAVA学科视频" << endl;
	}
};
//Python页面
class Python
{
public:
	void header()
	{
		cout << "首页、公开课、登录、注册...（公共头部）" << endl;
	}
	void footer()
	{
		cout << "帮助中心、交流合作、站内地图...(公共底部)" << endl;
	}
	void left()
	{
		cout << "Java,Python,C++...(公共分类列表)" << endl;
	}
	void content()
	{
		cout << "Python学科视频" << endl;
	}
};
//C++页面
class CPP 
{
public:
	void header()
	{
		cout << "首页、公开课、登录、注册...（公共头部）" << endl;
	}
	void footer()
	{
		cout << "帮助中心、交流合作、站内地图...(公共底部)" << endl;
	}
	void left()
	{
		cout << "Java,Python,C++...(公共分类列表)" << endl;
	}
	void content()
	{
		cout << "C++学科视频" << endl;
	}
};

void test01()
{
	//Java页面
	cout << "Java下载视频页面如下： " << endl;
	Java ja;
	ja.header();
	ja.footer();
	ja.left();
	ja.content();
	cout << "--------------------" << endl;

	//Python页面
	cout << "Python下载视频页面如下： " << endl;
	Python py;
	py.header();
	py.footer();
	py.left();
	py.content();
	cout << "--------------------" << endl;

	//C++页面
	cout << "C++下载视频页面如下： " << endl;
	CPP cp;
	cp.header();
	cp.footer();
	cp.left();
	cp.content();
}

int main() {
	test01();
	system("pause");
	return 0;
}
```
### 27.1.2 继承实现(减少重复代码)
**总结：**

 - 继承的好处：==可以减少重复的代码==
 - 语法：class 子类： 继承方式 父类  **class A : public B**;
 - A 类称为 **子类** 或 **派生类**
 - B 类称为 **父类** 或 **基类**

**派生类中的成员，包含两大部分**：

 - 一类是从基类继承过来的，一类是自己增加的成员
 - 从基类继承过过来的表现其共性，而新增的成员体现了其个性

```cpp
#include<iostream>
using namespace std;

//继承实现页面

//公共页面类
class BasePage
{
public:
	void header()
	{
		cout << "首页、公开课、登录、注册...（公共头部）" << endl;
	}
	void footer()
	{
		cout << "帮助中心、交流合作、站内地图...(公共底部)" << endl;
	}
	void left()
	{
		cout << "Java, Python, C++...(公共分类列表)" << endl;
	}
};

//继承的好处：减少重复代码
//语法：class 子类： 继承方式 父类
//子类 也称为 派生类
//父类 也称为 基类

//Java页面
class Java : public BasePage
{
public:
	void content()
	{
		cout << "JAVA 学科视频" << endl;
	}
};

//Python页面
class Python : public BasePage
{
public:
	void content()
	{
		cout << "Python 学科视频" << endl;
	}
};

//C++页面
class CPP : public BasePage
{
public:
	void content()
	{
		cout << "C++ 学科视频" << endl;
	}
};

void test01()
{
	//Java页面
	cout << "Java 下载视频页面如下： " << endl;
	Java ja;
	ja.header();
	ja.footer();
	ja.left();
	ja.content();
	cout << "--------------------" << endl;

	//Python页面
	cout << "Python 下载视频页面如下： " << endl;
	Python py;
	py.header();
	py.footer();
	py.left();
	py.content();
	cout << "--------------------" << endl;

	//C++页面
	cout << "C++ 下载视频页面如下： " << endl;
	CPP cp;
	cp.header();
	cp.footer();
	cp.left();
	cp.content();
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/bad1d863d88a4f2db828ed81c384c712.png)

## 27.2 继承方式

 - **继承的语法：`class 子类 : 继承方式  父类`**
 - **继承方式一共有三种：**
 - 公共继承
 - 保护继承
 - 私有继承
![在这里插入图片描述](https://img-blog.csdnimg.cn/468c6f7c34cc4a3a97aceb68a1855390.png)
 - 父类中私有内容，子类如论哪种继承都无法访问
### 27.2.1 公共继承

```cpp
// 公共继承
class Son1 :public Base1
{
public:
	void func()
	{
		m_A = 10; // 可访问 public权限,父类中的公共权限成员，到子类中依然是公共权限
		m_B = 10; // 可访问 protected权限，父类中的保护权限成员，到子类中依然是保护权限
		// m_C = 10; // 不可访问，父类中的私有权限成员，子类访问不到
	}
};

void test01()
{
	Son1 s1;
	s1.m_A = 100; //其他类只能访问到公共权限
	// s1.m_B = 100;//到了son1中m_B是保护权限，类外访问不到
}
```
### 27.2.2 保护继承

```cpp
// 保护继承
class Base2
{
public:
	int m_A;
protected:
	int m_B;
private:
	int m_C;
};

class Son2 :protected Base2
{
public:
	void func()
	{
		m_A = 100; // 可访问 protected权限，父类中的公共成员，到子类中变为保护权限
		m_B = 100; // 可访问 protected权限，父类中保护权限成员，到子类中变为保护权限
		// m_C = 100; // 父类中的私有成员子类不可访问
	}
};
void test02()
{
	Son2 s;
	// s.m_A = 100;//在Son2中m_A变为保护权限，因此类外不可访问
	// s.m_B = 100;//在Son2中m_B变为保护权限，因此类外不可访问
}
```
### 27.2.3 私有继承
```cpp
// 私有继承
class Base3
{
public:
	int m_A;
protected:
	int m_B;
private:
	int m_C;
};

class Son3 :private Base3
{
public:
	void func()
	{
		m_A = 100; // 可访问 private权限，父类中公共成员，在子类中变为 私有成员
		m_B = 100; // 可访问 private权限，父类中保护成员，在子类中变为 私有成员
		// m_C; // 父类中私有成员子类不可访问
	}
};

void test03()
{
	Son2 s;
	// s.m_A = 100;// 在Son3中m_A变为私有权限，因此类外不可访问
	// s.m_B = 100;// 在Son3中m_B变为私有权限，因此类外不可访问
}
```

 - 总程序

```cpp
#include<iostream>
using namespace std;

// 继承方式

class Base1
{
public:
	int m_A;
protected:
	int m_B;
private:
	int m_C;
};

// 公共继承
class Son1 :public Base1
{
public:
	void func()
	{
		m_A = 10; // 可访问 public权限，父类中的公共权限成员，到子类中依然是公共权限
		m_B = 10; // 可访问 protected权限，父类中的保护权限成员，到子类中依然是保护权限
		// m_C = 10; // 不可访问，父类中的私有权限成员，子类访问不到
	}
};

void test01()
{
	Son1 s1;
	s1.m_A = 100; //其他类只能访问到公共权限
	// s1.m_B = 100;//到了son1中m_B是保护权限，类外访问不到
}

// 保护继承
class Base2
{
public:
	int m_A;
protected:
	int m_B;
private:
	int m_C;
};

class Son2 :protected Base2
{
public:
	void func()
	{
		m_A = 100; // 可访问 protected权限，父类中的公共成员，到子类中变为保护权限
		m_B = 100; // 可访问 protected权限，父类中保护权限成员，到子类中变为保护权限
		// m_C = 100; // 父类中的私有成员子类不可访问
	}
};
void test02()
{
	Son2 s;
	// s.m_A = 100;//在Son2中m_A变为保护权限，因此类外不可访问
	// s.m_B = 100;//在Son2中m_B变为保护权限，因此类外不可访问
}

// 私有继承
class Base3
{
public:
	int m_A;
protected:
	int m_B;
private:
	int m_C;
};

class Son3 :private Base3
{
public:
	void func()
	{
		m_A = 100; // 可访问 private权限，父类中公共成员，在子类中变为 私有成员
		m_B = 100; // 可访问 private权限，父类中保护成员，在子类中变为 私有成员
		// m_C; // 父类中私有成员子类不可访问
	}
};

void test03()
{
	Son2 s;
	// s.m_A = 100;// 在Son3中m_A变为私有权限，因此类外不可访问
	// s.m_B = 100;// 在Son3中m_B变为私有权限，因此类外不可访问
}

class GrandSon3 :public Son3 // 孙子继承儿子
{
public:
	void func()
	{
		// Son3是私有继承，所以继承Son3的属性在GrandSon3中都无法访问到
		// m_A;// 到了Son3中m_A变为私有，即使是儿子，也访问不到
		// m_B;
		// m_C;
	}
};

int main()
{
	system("pause");
	return 0;
}
```
## 27.3 继承中的对象模型
**问题**：从父类继承过来的成员，哪些属于子类对象中？
**结论**

 - **父类中所有非静态成员属性都会被子类继承下去**
 - 父类中私有成员属性是被编译器给隐藏了，因此访问不到，但是确实被继承下去

```cpp
#include<iostream>
using namespace std;

// 继承中的对象模型

class Base
{
public:
	int m_A;
protected:
	int m_B;
private:
	int m_C; // 私有成员只是被隐藏了，但是还是会继承下去
};

// 公共继承
class Son :public Base
{
public:
	int m_D;
};

// 利用开发人员命令提示工具查看对象模型
// 跳转盘符 D：
// 跳转文件路径 cd 具体路径下
// 查看命名

void test01()
{
	// 父类中所有非静态成员属性都会被子类继承下去
	// 父类中私有成员属性是被编译器给隐藏了，因此访问不到，但是确实被继承下去
	cout << "sizeof Son = " << sizeof(Son) << endl;// 16
}

int main()
{
	test01();

	system("pause");
	return 0;
}
```
## 27.4 继承中构造与析构顺序
 - **问题**：子类继承父类后，当创建子类对象，也会调用父类的构造函数，父类和子类的构造和析构顺序是谁先谁后？
 - **总结**：继承中 **先调用父类构造函数**，**再调用子类构造函数**，析构顺序与构造相反，**先析构子类，再析构父类**。

```cpp
#include<iostream>
using namespace std;
//继承中的构造和析构顺序

class Base
{
public:
	Base()
	{
		cout << "Base 构造函数!" << endl;
	}
	~Base()
	{
		cout << "Base 析构函数!" << endl;
	}
};

class Son : public Base
{
public:
	Son()
	{
		cout << "Son  构造函数!" << endl;
	}
	~Son()
	{
		cout << "Son  析构函数!" << endl;
	}

};

void test01()
{
	// 继承中构造顺序和析构顺序如下:
	// 先调用父类构造函数，再调用子类构造函数，析构顺序与构造相反
	Son s;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/ffefea4302024c46afcbd79d8606c177.png)	
## 27.5 继承同名成员处理方法
**问题：当子类与父类出现同名的成员，如何通过子类对象，访问到子类或父类中同名的数据呢？**

### 27.5.1 同名成员属性
* **通过子类对象，访问子类同名成员   直接访问即可**
* **通过子类对象，访问父类中间同名成员，需要加作用域**
```cpp
// 同名成员属性处理方式
void test01()
{
	Son s;
	cout << "Son  下 m_A" << s.m_A << endl;

	// 如果通过子类对象，访问到父类中间同名成员，需要加作用域
	cout << "Base 下 m_A" << s.Base::m_A << endl;
}
```
### 27.5.2 同名成员函数
- **如果子类中出现和父类同名的成员函数，子类的同名成员函数会隐藏掉父类中所有同名成员函数**
- **如果想访问到父类中被隐藏的同名成员函数，需要加作用域**

```cpp
// 同名成员函数处理方式
void test02()
{
	Son s;
	s.func(); // 直接调用的是子类中的同名成员

	// 如何调用到父类中同名成员函数？加作用域
	s.Base::func();

	// 如果子类中出现和父类同名的成员函数,子类的同名成员函数会隐藏掉父类中所有同名成员函数
	// 如果想访问到父类中被隐藏的同名成员函数，需要加作用域
	s.Base::func(100);
}
```

 - 总程序

```cpp
#include<iostream>
using namespace std;

// 继承中同成员的处理
class Base
{
public:
	Base()
	{
		m_A = 100;
	}

	void func()
	{
		cout << "Base - func() 调用" << endl;
	}

	// 重载

	void func(int a)
	{
		cout << "Base - func(int a) 调用" << endl;
	}

	int m_A;
};

class Son :public Base
{
public:
	Son()
	{
		m_A = 200;
	}

	void func()
	{
		cout << "Son - func() 调用" << endl;
	}

	int m_A;
};

// 同名成员属性处理方式
void test01()
{
	Son s;
	cout << "Son  下 m_A: " << s.m_A << endl;

	// 如果通过子类对象，访问到父类中间同名成员，需要加作用域
	cout << "Base 下 m_A: " << s.Base::m_A << endl;
}

// 同名成员函数处理方式
void test02()
{
	Son s;
	s.func(); // 直接调用的是子类中的同名成员

	// 如何调用到父类中同名成员函数？加作用域
	s.Base::func();

	// 如果子类中出现和父类同名的成员函数,子类的同名成员函数会隐藏掉父类中所有同名成员函数
	// 如果想访问到父类中被隐藏的同名成员函数，需要加作用域
	s.Base::func(100);
}

int main()
{
	test01();
	test02();

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/37329a3f0d1740a7af355fc5b3ab25c8.png)	
## 27.6 继承同名静态成员处理方式
### 27.6.1 同名静态成员属性
#### 27.6.1.1 通过对象访问
```cpp
// 1. 通过对象来访问数据
cout << "通过对象访问：" << endl;
Son s;
cout << "Son 下 m_A = " << s.m_A << endl;
cout << "Base 下 m_A = " << s.Base::m_A << endl;
```
#### 27.6.1.2 通过类名访问
 - **第一个::代表通过类名方式访问  第二个::代表访问父类的作用域下**

```cpp
// 2. 通过类名访问数据
cout << "通过类名访问：" << endl;
cout << "Son 下 m_A = " << Son::m_A << endl;
// 第一个::代表通过类名方式访问  第二个::代表访问父类的作用域下
cout << "Base 下 m_A = " << Son::Base::m_A << endl;
```
### 27.6.2 同名静态成员属性
#### 27.6.2.1 通过对象访问

```cpp
// 1.通过对象访问
cout << "通过对象访问：" << endl;
Son s;
s.func();
s.Base::func();
```
#### 27.6.2.2 通过类名访问
 - **子类出现和父类同名的静态成员函数，也会隐藏父类中所有的同名成员函数**
 - 如果想**访问父类中被隐藏同名成员，需要加作用域**

```cpp
// 通过类名访问
cout << "通过类名访问：" << endl;
Son::func();
Son::Base::func();
```

 - 总结：**同名静态成员处理方式和非静态处理方式一样，只不过有两种访问的方式（通过对象 和 通过类名**

```cpp
#include<iostream>
using namespace std;

//继承中同名静态成员处理方式
class Base
{
public:
	static int m_A;

	static void func()// 成员函数
	{
		cout << "Base - static void func()" << endl;
	}
	static void func(int a)// 成员函数(重载)
	{
		cout << "Base - static void func(int a)" << endl;
	}
};
int  Base::m_A = 100;

class Son :public Base
{
public:
	static int m_A;// 需要赋初值

	static void func()// 成员函数
	{
		cout << "Son - static void func()" << endl;
	}
};
int Son::m_A = 200;

// 同名静态成员属性
void test01()
{
	// 1. 通过对象来访问
	cout << "通过对象访问：" << endl;
	Son s;
	cout << "Son 下 m_A = " << s.m_A << endl;
	cout << "Base 下 m_A = " << s.Base::m_A << endl;
	cout << endl;

	// 2. 通过类名访问
	cout << "通过类名访问：" << endl;
	cout << "Son 下 m_A = " << Son::m_A << endl;
	// 第一个::代表通过类名方式访问  第二个::代表访问父类的作用域下
	cout << "Base 下 m_A = " << Son::Base::m_A << endl;
	cout << endl;
}

// 同名静态成员函数
void test02()
{
	// 1.通过对象访问
	cout << "通过对象访问：" << endl;
	Son s;
	s.func();
	s.Base::func();
	cout << endl;

	// 通过类名访问
	cout << "通过类名访问：" << endl;
	Son::func();
	Son::Base::func();

	// 子类出现和父类同名的静态成员函数，也会隐藏父类中所有的同名成员函数
	// 如果想访问父类中被隐藏同名成员，需要加作用域
	Son::Base::func(100);
	cout << endl;
}

int main()
{
	test01();
	test02();

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/78cc52ee719642929a9ab8a4a7c0610e.png)
## 27.7 多继承语法(不建议用)

 - C++允许**一个类继承多个类**
 - 语法：` class 子类 ：继承方式 父类1 ， 继承方式 父类2...`
 - 多继承可能会引发父类中有同名成员出现，需要加作用域区分
 - **C++实际开发中不建议用多继承**

```cpp
#include<iostream>
using namespace std;

// 多继承语法(不建议使用)
class Base1
{
public:
	// 无参构造函数
	Base1()
	{
		m_A = 100;
	}
	int m_A;
};

class Base2
{
public:
	// 无参构造函数
	Base2()
	{
		m_A = 200;
	}
	int m_A;
};

// 子类 需要继承Base1和Base2
// 语法：class 子类：继承方式1 父类1，继承方式2 父类2
class Son :public Base1, public Base2
{
public:
	Son()
	{
		m_C = 300;
		m_D = 400;
	}

	int m_C;
	int m_D;
};

void test01()
{
	Son s;
	cout << "sizeof Son = " << sizeof(s) << endl;// 16,包括继承父类的两个

	// 当父类中出现了重名的成员，需要加作用域区分
	cout << "Base1::m_A = " << s.Base1::m_A << endl;// 100
	cout << "Base2::m_A = " << s.Base2::m_A << endl;// 200
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
## 27.8 菱形继承
**菱形继承概念：**
 - 两个派生类继承同一个基类
 - 又有某个类同时继承者两个派生类
 - 	这种继承被称为菱形继承，或者钻石继承
![在这里插入图片描述](https://img-blog.csdnimg.cn/9165734edacb4c11af90a5ca363d98eb.png)

**菱形继承问题：**
 - 羊继承了动物的数据，驼同样继承了动物的数据，当草泥马使用数据时，就会产生二义性
 -  草泥马**继承自动物的数据继承两份**，其实我们应该清楚，这份数据我们只需要一份就可以

**解决方法：**

 - 利用**虚继承**可以解决菱形继承的问题
 - 在继承之前加上关键字 **virtual** 变为**虚继承**
 - **Animal类 称为虚基类**

```cpp
#include<iostream>
using namespace std;

//动物类
class Animal
{
public:
	int m_Age;
};

// 利用虚继承可以解决菱形继承的问题
// 在继承之前加上关键字 virtual 变为虚继承
// Animal类 称为 虚基类

// 羊类
class Sheep :virtual public Animal
{
};

// 驼类
class Tuo :virtual public Animal
{
};

//羊驼类
class SheepTuo :public Sheep, public Tuo
{
};

void test01()
{
	SheepTuo st;

	st.Sheep::m_Age = 18;
	st.Tuo::m_Age = 28;
	// 当出现菱形继承的时候，两个父类拥有相同数据，需要加作用域区分
	cout << "st.Sheep::m_Age = " << st.Sheep::m_Age << endl;
	cout << "st.Tuo::m_Age = " << st.Tuo::m_Age << endl;

	// 这份数据知道，只要有一份就可以了，菱形继承导致数据有两分，导致资源浪费
}

int main()
{
	system("pause");
	return 0;
}
```

# 核心7 类和对象_多态、文件操作(重难点)

# 28 多态(子类重写父类中的虚函数)
**多态是C++面向对象三大特性之一**

> 多态分为两类

* 静态多态: 函数重载 和 运算符重载属于静态多态，复用函数名
* **动态多态: 派生类和虚函数实现运行时多态**

> 静态多态和动态多态区别：

* 静态多态的函数地址早绑定  -  编译阶段确定函数地址
* **动态多态的函数地址晚绑定  -  运行阶段确定函数地址**

## 28.1 多态基本语法

> 动态多态满足条件

* **有继承关系**
* **子类重写父类中的虚函数**，重写是函数名相同，函数返回值类型相同，形参列表中东西相同。
* 重写时子类的 virtual 可写可不写

> 动态多态使用条件

 * **父类指针或引用指向子类对象 Animal &animal = cat(引用)**
 * 重写：**函数返回值类型  函数名 参数列表 完全一致**称为重写

```cpp
#include<iostream>
using namespace std;

// 动物类
class Animal
{
public:
	// 虚函数 virtual
	virtual void speak()
	{
		cout << "动物在说话" << endl;
	}
};

// 猫类
class Cat :public Animal
{
public:
	// 重写：函数返回值类型 函数名 参数列表 三个完全相同
	void speak()
	{
		cout << "小猫在说话" << endl;
	}
};

//狗类
class Dog :public Animal
{
public:
	void speak()
	{
		cout << "小狗在说话" << endl;
	}
};

// 我们希望传入什么对象，那么就调用什么对象的函数
// 如果函数地址在编译阶段就能确定，那么静态联编
// 如果函数地址在运行阶段才能确定，就是动态联编

// 执行说话的函数
// 地址早绑定，在编译阶段就确定函数地址
// 如果想执行让猫说话，那么这个函数地址就不能提前绑定，需要在运行阶段进行绑定，地址晚绑定
void dospeak(Animal& animal)// 类似Animal &animal=cat，父类引用指向子类的传递对象
{
	animal.speak();// 加了virtual后，由于加入的对象不同，确定不同函数地址
}

void test01()
{
	Cat cat;
	dospeak(cat);

	Dog dog;
	dospeak(dog);
}

void test02()
{
	cout << "sizeof Animal = " << sizeof(Animal) << endl;
}

int main()
{
	test01();
	test02();

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/25437a39d52e4120bd6ab787d7456d81.png)
## 28.2 多态原理剖析
![在这里插入图片描述](https://img-blog.csdnimg.cn/4c3f32194d9c43fa8d79a0e6dfcbba77.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/819a81998bd44f89bc75cde52879f34e.png)

## 28.3 多态案例1 计算机类
案例描述：分别利用普通写法和多态技术，设计实现两个操作数进行运算的计算器类

**多态的优点**：

* 代码组织结构清晰
* 可读性强
* 利于前期和后期的扩展以及维护

### 28.3.1普通写法
 - 如果想扩展新的功能，需要修改源码
 - 在真实开发中，提倡 开闭原则
 - **开闭原则：对扩展进行开放，对修改进行关闭**

```cpp
// 普通写法
class Calculator
{
public:
	// 获取运算结果
	int getResult(string oper)// 传入操作符
	{
		if (oper == "+")
		{
			return m_Num1 + m_Num2;
		}
		else if (oper == "-")
		{
			return m_Num1 - m_Num2;
		}
		else if (oper == "*")
		{
			return m_Num1 * m_Num2;
		}
		// 如果想扩展新的功能，需要修改源码
		// 在真实开发中，提倡 开闭原则
		// 开闭原则：对扩展进行开放，对修改进行关闭
	}

	int m_Num1;//操作数1
	int m_Num2;//操作数2
};

void test01()
{
	//创建计算器对象
	Calculator c;
	c.m_Num1 = 10;
	c.m_Num2 = 10;

	cout << c.m_Num1 << " + " << c.m_Num2 << " = " << c.getResult("+") << endl;
	cout << c.m_Num1 << " - " << c.m_Num2 << " = " << c.getResult("-") << endl;
	cout << c.m_Num1 << " * " << c.m_Num2 << " = " << c.getResult("*") << endl;
}
```

### 28.3.2 多态写法

**多态好处：**
1. 组织结构清晰
2. 可读性强
3. 对于前期和后期扩展以及维护性高

总结：**C++开发提倡利用多态设计程序架构，因为多态优点很多**

```cpp
#include<iostream>
#include<string>
using namespace std;

// 分别利用普通写法和多态技术实现计算器

// 普通写法
class Calculator
{
public:
	// 获取运算结果
	int getResult(string oper)// 传入操作符
	{
		if (oper == "+")
		{
			return m_Num1 + m_Num2;
		}
		else if (oper == "-")
		{
			return m_Num1 - m_Num2;
		}
		else if (oper == "*")
		{
			return m_Num1 * m_Num2;
		}
		// 如果想扩展新的功能，需要修改源码
		// 在真实开发中，提倡 开闭原则
		// 开闭原则：对扩展进行开放，对修改进行关闭
	}

	int m_Num1;// 操作数1
	int m_Num2;// 操作数2
};

void test01()
{
	// 创建计算器对象
	Calculator c;
	c.m_Num1 = 10;
	c.m_Num2 = 10;

	cout << c.m_Num1 << " + " << c.m_Num2 << " = " << c.getResult("+") << endl;
	cout << c.m_Num1 << " - " << c.m_Num2 << " = " << c.getResult("-") << endl;
	cout << c.m_Num1 << " * " << c.m_Num2 << " = " << c.getResult("*") << endl;
}

// 多态好处：
// 1.组织结构清晰
// 2.可读性强
// 3.对于前期和后期扩展以及维护性高

// 利用多态实现计算器

// 实现计算器的抽象类
class AbstractCalculator
{
public:
	// 写成虚函数
	virtual int getResult()
	{
		return 0;
	}

	int m_Num1;
	int m_Num2;
};

//加法计算器类
class AddCalculator :public AbstractCalculator
{
public:
	int getResult()
	{
		return m_Num1 + m_Num2;
	}
};

//减法计算器类
class SubCalculator :public AbstractCalculator
{
public:
	int getResult()
	{
		return m_Num1 - m_Num2;
	}
};

//乘法计算器类
class MulCalculator :public AbstractCalculator
{
public:
	int getResult()
	{
		return m_Num1 * m_Num2;
	}
};

void test02()
{
	// 多态使用条件
	// 父类指针或者引用指向子类对象

	// new数据设置在堆区(用父类的指针)
	
	// 加法运算
	// 创建一个加法计算器的对象，用父类的指针指向子类的对象
	AbstractCalculator* abc = new AddCalculator;// abc 为指针
	abc->m_Num1 = 100;
	abc->m_Num2 = 100;

	cout << abc->m_Num1 << " + " << abc->m_Num2 << " = " << abc->getResult() << endl;
	//用完后手动释放堆区数据，数据释放了，但abc还是父类的指针
	delete abc;

	//减法运算
	abc = new SubCalculator;
	abc->m_Num1 = 100;
	abc->m_Num2 = 100;

	cout << abc->m_Num1 << " - " << abc->m_Num2 << " = " << abc->getResult() << endl;
	delete abc;

	//乘法运算
	abc = new MulCalculator;
	abc->m_Num1 = 100;
	abc->m_Num2 = 100;

	cout << abc->m_Num1 << " * " << abc->m_Num2 << " = " << abc->getResult() << endl;
	delete abc;
}

int main()
{
	test01();
	cout << endl;
	test02();

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/ee158f93999f4f09b266037e4f21909a.png)
## 28.4 纯虚函数和抽象类(难点)
在多态中，通常父类中虚函数的实现是毫无意义的，主要都是调用子类重写的内容，因此可以将虚函数改为**纯虚函数**。

 - 纯虚函数语法：`virtual 返回值类型 函数名 （参数列表）= 0 ;`
 - 当类中有了纯虚函数，这个类也称为==抽象类==

**抽象类特点**：

 * 无法实例化对象
 * 子类必须重写抽象类中的纯虚函数，否则也属于抽象类

```cpp
#include<iostream>
using namespace std;

// 多态的意义是让子类重写父类中的虚函数
// 纯虚函数 和 抽象类
class Base
{
public:
	// 只要有一个纯虚函数，这个类称为抽象类
	// 抽象类特点：
	// 1.无法实例化对象
	// 2.抽象类的子类 必须重写父类中的纯虚函数，否则也属于抽象类，无法实例化对象
	virtual void func() = 0;// 纯虚函数 语法

};

class Son :public Base // 继承
{
public:
	virtual void func() // 重写父类中的纯虚函数
	{
		cout << "func 函数调用" << endl;
	};
};

void test01()
{
	// Base b;// 抽象类是无法实例化对象
	// new Base;// 抽象类是无法实例化对象

	Son s;// 子类必须重写父类中的纯虚函数(子类加virtual)，否则无法实例化对象

	Base* base = new Son;// new 什么对象，就调用什么对象 func 函数
	base->func(); // 调用子类 func 函数
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/5f38eb9371c4442788a9da380527496f.png)

## 28.5 多态案例2 制作饮品
**案例描述：**

 - 制作饮品的大致流程为：**煮水 -  冲泡 - 倒入杯中 - 加入辅料**
 - 利用多态技术实现本案例，提供抽象制作饮品基类，提供子类制作咖啡和茶叶
![在这里插入图片描述](https://img-blog.csdnimg.cn/b58e6057769d4ae8998bbbbff90a4c87.png)
```cpp
#include<iostream>
using namespace std;

// 多态案例2 制作饮品
class AbstractDrinking
{
public:
	// 写成纯虚函数，不做任何处理
	// 煮水
	virtual void Boil() = 0;
	// 冲泡
	virtual void Brew() = 0;
	// 倒入杯中
	virtual void PourInCup() = 0;
	// 加入辅料
	virtual void PutSomething() = 0;
	// 制作饮品
	void makeDrink()
	{
		Boil();
		Brew();
		PourInCup();
		PutSomething();
	}
};

// 制作咖啡
class Coffee :public AbstractDrinking
{
public:
	// 煮水
	virtual void Boil()
	{
		cout << "煮农夫山泉" << endl;
	}
	// 冲泡
	virtual void Brew()
	{
		cout << "冲泡咖啡" << endl;
	}
	// 倒入杯中
	virtual void PourInCup()
	{
		cout << "倒入杯中" << endl;
	}
	// 加入辅料
	virtual void PutSomething()
	{
		cout << "加入糖和牛奶" << endl;
	}
};

// 制作茶叶
class Tea :public AbstractDrinking
{
public:
	// 煮水
	virtual void Boil()
	{
		cout << "煮农夫山泉" << endl;
	}
	// 冲泡
	virtual void Brew()
	{
		cout << "冲泡茶叶" << endl;
	}
	// 倒入杯中
	virtual void PourInCup()
	{
		cout << "倒入杯中" << endl;
	}
	// 加入辅料
	virtual void PutSomething()
	{
		cout << "加入枸杞" << endl;
	}
};

// 制作函数
void doWork(AbstractDrinking* abs)// 父类的指针
{
	abs->makeDrink();
	// 制作完delete
	delete abs;// 堆区数据手动开辟，手动释放
}

void test01()
{
	// 制作咖啡
	doWork(new Coffee);// AbstractDrinking *abs = new Coffee

	cout << " --------------- " << endl;

	// 制作茶叶
	doWork(new Tea);
}

int main()
{
	test01();

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/3f6c32c0c604441c8ed74d11b4c6f989.png)
## 28.6 虚析构和纯虚析构(难点)

 - 多态使用时，如果子类中有属性开辟到堆区，那么父类指针在释放时无法调用到子类的析构代码
 - 解决方式：将父类中的析构函数改为**虚析构**或者**纯虚析构**

**虚析构和纯虚析构共性：**

* 可以解决父类指针释放子类对象，**如果父类没有写成虚析构或者纯虚析构，就不会走子类的虚构代码。**
* 都需要有具体的函数实现，就是虚析构、纯虚析构要进行函数实现。

**虚析构和纯虚析构区别：**
* 如果是**纯虚析构，该类属于抽象类，无法实例化对象**

虚析构语法：`virtual ~类名(){}`

纯虚析构语法：**类内声明** —— ` virtual ~类名() = 0;` **类外实现** —— `类名::~类名(){}`

> 总结：

 - 虚析构或纯虚析构就是用来解决通过父类指针释放子类对象
 - 如果子类中没有堆区数据，可以不写为虚析构或纯虚析构。有指针情况就会有堆区
 - **拥有纯虚析构函数的类也属于抽象类**

```cpp
#include<iostream>
#include<string>
using namespace std;

// 虚析构和纯虚析构 —— 解决子类中的代码调用不到的问题，存在指针类型，在堆区
class Animal
{
public:

	Animal() // 无参构造函数调用
	{
		cout << "Animal 构造函数调用" << endl;
	}

	// 利用虚析构可以解决 父类指针释放子类对象时不干净的问题
	virtual ~Animal() // 析构函数，虚析构，这样Cat析构函数就会调用出来
	{
		cout << "Animal 虚析构函数调用" << endl;
	}

	// 纯虚析构, 与虚析构只能有一个存在, 需要声明也需要实现
	// 有了纯虚析构之后，这个类也属于抽象类，无法实例化对象
	// virtual ~Animal() = 0;
	
	// 纯虚函数，与纯虚析构不同，不需要实现
	virtual void speak() = 0;
};

// Animal 下的纯虚析构
//Animal::~Animal()
//{
//	cout << "Animal 纯虚析构函数调用" << endl;
//}

class Cat :public Animal
{
public:

	Cat(string name)// 有参构造函数
	{
		cout << "Cat 构造函数调用" << endl;
		m_Name = new string(name);// new 一个string,返回的是string指针
	}

	virtual void speak() // 子类重写父类
	{
		cout << *m_Name << " 小猫在说话" << endl;
	}

	~Cat() // 析构函数
	{
		if (m_Name != NULL)
		{
			cout << "Cat 析构函数调用" << endl;
			delete m_Name;
			m_Name == NULL;
		}
	}

public:
	string *m_Name;// 让小猫的名称创建在堆区
};

void test01()
{
	Animal* animal = new Cat("Tom");
	animal->speak();
	// 父类指针在析构时，不会调用子类中析构函数，导致子类如果有堆区的属性，出现内存的泄露情况
	delete animal;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/a6ed57f93e8d4f8086c216d3dba9fcf4.png)

### 28.6.1 纯虚函数和纯虚析构的区别

 - **纯虚析构**, 与虚析构只能有一个存在, **需要声明也需要实现**
 - **有了纯虚析构之后，这个类也属于抽象类，无法实例化对象**
 - **纯虚函数**，与纯虚析构不同，**只要声明不需要实现**

```cpp
	// 纯虚析构, 与虚析构只能有一个存在, 需要声明也需要实现
	// virtual ~Animal() = 0;
	
	// Animal 下的纯虚析构
	//Animal::~Animal()
	//{
	//	cout << "Animal 纯虚析构函数调用" << endl;
	//}
	
	// 纯虚函数，与纯虚析构不同，不需要实现
	virtual void speak() = 0;
```

## 28.7 多态案例3 电脑组装(重难点)
**案例描述：**
 - 电脑主要组成部件为 **CPU（用于计算），显卡（用于显示），内存条（用于存储）**
 - **将每个零件封装出抽象基类，并且提供不同的厂商生产不同的零件**，例如Intel厂商和Lenovo厂商
 - **创建电脑类提供让电脑工作的函数，并且调用每个零件工作的接口**
 - 测试时组装三台不同的电脑进行工作

![在这里插入图片描述](https://img-blog.csdnimg.cn/9964a8ef579d4157add4bd780ffb718f.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/8bbd7d35a5aa452cb1d16194210ac70e.png)
### 28.7.1 抽象每个零件的类

```cpp
// 抽象出每个零件的类
// 1.抽象CPU类 
class CPU	// 抽象类
{
public:
	// 抽象计算函数
	virtual void calculate() = 0;
};

// 2.抽象显卡类
class VideoCard // 抽象类
{
public:
	// 抽象显示函数
	virtual void display() = 0;
};

// 3.抽象内存条类
class Memory // 抽象类
{
public:
	// 抽象存储函数
	virtual void storage() = 0;
};
```
### 28.7.2 电脑类
```cpp
// 电脑类
class Computer
{
	// 构造函数中传入三个零件指针
public:
	// 有参构造
	Computer(CPU* cpu, VideoCard* vc, Memory* mem)
	{
		m_cpu = cpu;
		m_vc = vc;
		m_mem = mem;
	}

	// 提供工作函数
	void work()
	{
		// 让零件工作起来，调用接口
		m_cpu->calculate();
		m_vc->display();
		m_mem->storage();
	}

	// 提供析构函数 释放3个电脑零件
	~Computer()
	{
		// 释放CPU零件
		if (m_cpu != NULL)
		{
			delete m_cpu;
			m_cpu = NULL;
		}
		// 释放显卡零件
		if (m_vc != NULL)
		{
			delete m_vc;
			m_vc = NULL;
		}
		// 释放内存条零件
		if (m_mem != NULL)
		{
			delete m_mem;
			m_mem = NULL;
		}
	}
private:
	CPU* m_cpu;// CPU的零件指针
	VideoCard* m_vc;// 显卡的零件指针
	Memory* m_mem;// 内存条零件指针
};
```
### 28.7.3 具体零件厂商
```cpp
// Inter厂商
class InterCpu :public CPU
{
public:
	virtual void calculate()
	{
		cout << "Inter CPU开始计算" << endl;
	}
};

class InterVideoCard :public VideoCard
{
public:
	virtual void display()
	{
		cout << "Inter 显卡开始显示" << endl;
	}
};

class InterMemory :public Memory
{
public:
	virtual void storage()
	{
		cout << "Inter 内存条开始存储" << endl;
	}
};

// 联想厂商
class LenovoCpu :public CPU
{
public:
	virtual void calculate()
	{
		cout << "Lenovo CPU开始计算" << endl;
	}
};

class LenovoVideoCard :public VideoCard
{
public:
	virtual void display()
	{
		cout << "Lenovo 显卡开始显示" << endl;
	}
};

class LenovoMemory :public Memory
{
public:
	virtual void storage()
	{
		cout << "Lenovo 内存条开始存储" << endl;
	}
};
```
### 28.7.4 创建电脑

```cpp
#include<iostream>
using namespace std;

// 抽象出每个零件的类

// 1.抽象CPU类 
class CPU	// 抽象类
{
public:
	// 抽象计算函数
	virtual void calculate() = 0;
};

// 2.抽象显卡类
class VideoCard // 抽象类
{
public:
	// 抽象显示函数
	virtual void display() = 0;
};

// 3.抽象内存条类
class Memory // 抽象类
{
public:
	// 抽象存储函数
	virtual void storage() = 0;
};

// 电脑类
class Computer
{
	// 构造函数中传入三个零件指针
public:
	Computer(CPU* cpu, VideoCard* vc, Memory* mem)
	{
		m_cpu = cpu;
		m_vc = vc;
		m_mem = mem;
	}

	// 提供工作函数
	void work()
	{
		// 让零件工作起来，调用接口
		m_cpu->calculate();
		m_vc->display();
		m_mem->storage();
	}

	// 提供析构函数 释放3个电脑零件
	~Computer()
	{
		// 释放CPU零件
		if (m_cpu != NULL)
		{
			delete m_cpu;
			m_cpu = NULL;
		}
		// 释放显卡零件
		if (m_vc != NULL)
		{
			delete m_vc;
			m_vc = NULL;
		}
		// 释放内存条零件
		if (m_mem != NULL)
		{
			delete m_mem;
			m_mem = NULL;
		}
	}

private:
	// 电脑的类中有三个指针维护三个零件
	CPU* m_cpu;// CPU的零件指针
	VideoCard* m_vc;// 显卡的零件指针
	Memory* m_mem;// 内存条零件指针
};

// 具体零件厂商

// Inter厂商
class InterCpu :public CPU
{
public:
	virtual void calculate()
	{
		cout << "Inter CPU开始计算" << endl;
	}
};

class InterVideoCard :public VideoCard
{
public:
	virtual void display()
	{
		cout << "Inter 显卡开始显示" << endl;
	}
};

class InterMemory :public Memory
{
public:
	virtual void storage()
	{
		cout << "Inter 内存条开始存储" << endl;
	}
};

// 联想厂商
class LenovoCpu :public CPU
{
public:
	virtual void calculate()
	{
		cout << "Lenovo CPU开始计算" << endl;
	}
};

class LenovoVideoCard :public VideoCard
{
public:
	virtual void display()
	{
		cout << "Lenovo 显卡开始显示" << endl;
	}
};

class LenovoMemory :public Memory
{
public:
	virtual void storage()
	{
		cout << "Lenovo 内存条开始存储" << endl;
	}
};

// 组装不同的电脑

void test01()
{
	//第一台电脑组装，CPU为父类，InterCpu是子类
	CPU* intelCpu = new InterCpu;// 多态技术，用父类的指针指向子类对象
	VideoCard* intelCard = new InterVideoCard;
	Memory* intelMem = new InterMemory;
	cout << "第一台电脑开始工作：" << endl;

	//创建第一台电脑
	Computer* computer1 = new Computer(intelCpu, intelCard, intelMem);
	computer1->work();
	delete computer1;
	cout << "-----------------------" << endl;

	cout << "第二台电脑开始工作：" << endl;
	//第二台电脑组装
	Computer* computer2 = new Computer(new LenovoCpu, new LenovoVideoCard, new LenovoMemory);;
	computer2->work();
	delete computer2;
	cout << "-----------------------" << endl;

	cout << "第三台电脑开始工作：" << endl;
	//第三台电脑组装
	Computer* computer3 = new Computer(new LenovoCpu, new InterVideoCard, new LenovoMemory);;
	computer3->work();
	delete computer3;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/f049076a9165462d8863d3a2a042463a.png)
# 29 文件操作
程序运行时产生的数据都属于临时数据，程序一旦运行结束都会被释放。通过**文件可以将数据持久化**，C++中对文件操作需要包含头文件 ==&lt; fstream &gt;==

**文件类型**分为两种：

1. **文本文件**     -  文件以文本的**ASCII码**形式存储在计算机中
2. **二进制文件** -  文件以文本的**二进制**形式存储在计算机中，用户一般不能直接读懂它们

**操作文件的三大类**:

1. ofstream：写操作
2. ifstream： 读操作
3. fstream ： 读写操作

## 29.1 写文件
  写文件步骤如下：

1. **包含头文件：\#include <fstream\>**

2. **创建流对象 ：ofstream ofs**

3. **打开文件：ofs.open("文件路径",打开方式)**

4. **写数据：ofs << "写入的数据"**

5. **关闭文件：ofs.close()**


文件打开方式：

| 打开方式    | 解释                       |
| ----------- | -------------------------- |
| ios::in     | 为读文件而打开文件         |
| ios::out    | 为写文件而打开文件         |
| ios::ate    | 初始位置：文件尾           |
| ios::app    | 追加方式写文件             |
| ios::trunc  | 如果文件存在先删除，再创建 |
| ios::binary | 二进制方式                 |

**注意：** 文件打开方式可以配合使用，利用|操作符

**例如：**用二进制方式写文件 `ios::binary |  ios:: out`

```cpp
#include<iostream>
#include <fstream>// 头文件包含
using namespace std;

// 文本文件 写文件
void test01()
{
	// 1.包含头文件 fstream

	// 2.创建流对象

	ofstream ofs;

	// 3.指定打开的方式   文件名，写文件
	// 不指定路径的话，txt在文档文件下，右击打开文件夹
	ofs.open("test.txt", ios::out);

	// 4.写内容
	ofs << "姓名：张三" << endl;
	ofs << "性别：男" << endl;
	ofs << "年龄：18" << endl;

	// 5.关闭文件
	ofs.close();
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
总结：

* 文件操作**必须包含头文件 fstream**
* 读文件可以**利用 ofstream  ，或者fstream类**
* 打开文件时候**需要指定操作文件的路径，以及打开方式**
* 利用 << 可以向文件中写数据
* 操作完毕，要关闭文件。

## 29.2 读文件
读文件步骤如下：

1. 包含头文件：\#include <fstream\>

2. 创建流对象：ifstream ifs;

3. 打开文件并判断文件是否打开成功：ifs.open("文件路径",打开方式);

4. 读数据：四种方式读取

5. 关闭文件：ifs.close();


```cpp
#include<iostream>
#include <fstream>
#include<string>
using namespace std;

// 文本文件 读文件
void test01()
{
	// 1.包含头文件 <fstream>

	// 2.创建流对象
	ifstream ifs;

	// 3.打开文件并且判断是否打开成功
	ifs.open("test.txt", ios::in);

	if (!ifs.is_open())// 反过来判断 open 失败
	{
		cout << "文件打开失败" << endl;
		return;
	}

	// 4.读数据

	//第一种
	char buf[1024] = { 0 };
	while (ifs >> buf)
	{
		cout << buf << endl;
	}

	// 第二种
	char buf[1024] = { 0 };// buf指向数组的首地址
	while (ifs.getline(buf, sizeof(buf)))
	{
		cout << buf << endl;
	}

	//第三种
	/*string buf;
	while (getline(ifs, buf))
	{
		cout << buf << endl;
	}*/

	//第四种
	char c;
	while (c = ifs.get() != EOF)//EOF表示end of file 文件尾部
	{
		cout << c;
	}

	//5.关闭文件
	ifs.close();
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

总结：

- 读文件可以利用 ifstream  ，或者fstream类
- 利用is_open函数可以判断文件是否打开成功
- close 关闭文件 

## 29.3 二进制写文件

 - 以二进制的方式对文件进行读写操作，打开方式要指定为 ==ios::binary==
 - 二进制方式写文件主要利用流对象调用成员函数write函数原型 ：`ostream& write(const char *
   buffer,int len);`
 - 参数解释：字符指针buffer指向内存中一段存储空间。len是读写的字节数

总结：

* 文件输出流对象 可以通过write函数，以二进制方式写数据

```cpp
#include<iostream>
#include <fstream>
#include<string>
using namespace std;

class Person
{
public:
	char m_Name[64];// 尽量不用c++的string
	int m_Age;
};

// 二进制文件  写文件
void test01()
{
	// 1、包含头文件

	// 2、创建输出流对象
	ofstream ofs("person.txt", ios::out | ios::binary);

	// 3、打开文件
	//ofs.open("person.txt", ios::out | ios::binary);

	Person p = { "张三"  , 18 };

	// 4、写文件
	ofs.write((const char*)&p, sizeof(p));

	// 5、关闭文件
	ofs.close();
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
## 29.4 二进制读文件

 - 二进制方式读文件主要利用流对象调用成员函数read
 - 函数原型：`istream& read(char *buffer,int len);`
 - 参数解释：字符指针buffer指向内存中一段存储空间，len是读写的字节数。
 - 文件输入流对象 可以通过read函数，以二进制方式读数据

```cpp
#include<iostream>
#include<fstream>
#include<string>
using namespace std;

class Person
{
public:
	char m_Name[64];// 姓名
	int m_Age;// 年龄
};

// 二进制文件 读文件
void test01()
{
	// 1.包含头文件

	// 2.创建流对象
	ifstream ifs;


	// 3.打开文件 判断文件是否打开成功
	ifs.open("person.txt", ios::in | ios::binary);

	if (!ifs.is_open())
	{
		cout << "文件打开失败" << endl;
		return;
	}

	// 4.读文件
	Person p;
	ifs.read((char*)&p, sizeof(Person));
	cout << "姓名：" << p.m_Name << "年龄" << p.m_Age << endl;

	// 5.关闭文件
	ifs.close();
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

# 提高1 泛型编程_模板

# 30 函数模板

模板就是建立**通用的模具**，大大**提高复用性**。例如生活中的模板
一寸照片模板：
![在这里插入图片描述](https://img-blog.csdnimg.cn/3843fd2c9cee4a569f0dfa6f8f4c1d1a.png)模板的特点：

* 模板不可以直接使用，它只是一个框架
* 模板的通用并不是万能的
## 30.1 函数模板概念
* C++另一种编程思想称为 ==泛型编程== ，主要利用的技术就是模板

* C++提供两种模板机制:**函数模板**和**类模板** 

## 30.2 函数模板语法

 - **函数模板作用**：建立一个通用函数，其**函数返回值类型和形参类型可以不具体制定**，用一个**虚拟的类型**来代表。void func(int a) ——> 变成 template\<typename T>。在使用时才进行具体的说明。T 是通用的数据类型，typename 通常用 class 代替

> **语法：**
```C++
template<typename T>
函数声明或定义
```
> **解释：**

 - template  ---  声明创建模板
 - typename  --- 表面其后面的符号是一种数据类型，可以用class代替
 - T    ---   通用的数据类型，名称可以替换，通常为大写字母

![在这里插入图片描述](https://img-blog.csdnimg.cn/0b2265a16b754470bfafc12bf9480c0b.png)
### 30.2.1 传统数字交换

```cpp
// 交换两个整型函数
void swapInt(int& a, int& b)
{
	int temp = a;
	a = b;
	b = temp;
}

// 交换两个浮点型函数
void swapDouble(double& a, double& b)
{
	double temp = a;
	a = b;
	b = temp;
}
```

### 30.2.2 函数模板数字交换
总结

* 函数模板利用关键字 template
* 使用函数模板有两种方式：自动类型推导、显示指定类型
* 模板的目的是为了**提高复用性，将类型参数化**(比如 int double类型 ——> 用参数 T 表示)

```cpp
// 函数模板
// 声明一个模板，告诉编译器后面的代码中紧跟着T不要报错，T是一个通用数据类型
template<typename T>
void mySwap(T& a, T& b)
{
	T temp = a;
	a = b;
	b = temp;
}
```

> 使用函数模板的方法

 1. **自动类型推导**

```cpp
	// 1、自动类型推导
	int a = 10;
	int b = 20;
	// swapInt(a, b);
	mySwap(a, b);// T 推导出是int类型
	cout << "a = " << a << endl;
	cout << "b = " << b << endl;
```

 2. **显示指定类型**

```cpp
	// 2、显示指定类型
	int c = 30;
	int d = 40;
	mySwap<int>(c, d);// 这里 T 的数据类型就是 int
	cout << "c = " << c << endl;
	cout << "d = " << d << endl;
```

 - 总程序

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
#include<map>
using namespace std;

// 函数模板 —— 使数据类型参数化

// 交换两个整型函数
void swapInt(int& a, int& b)
{
	int temp = a;
	a = b;
	b = temp;
}

// 交换两个浮点型函数
void swapDouble(double& a, double& b)
{
	double temp = a;
	a = b;
	b = temp;
}

// 函数模板
// 声明一个模板，告诉编译器后面的代码中紧跟着T不要报错，T是一个通用数据类型
template<typename T>
void mySwap(T& a, T& b)
{
	T temp = a;
	a = b;
	b = temp;
}

void test01()
{
	// 利用函数模板交换
	// 两种方式使用函数模板
	// 1、自动类型推导
	int a = 10;
	int b = 20;
	// swapInt(a, b);
	mySwap(a, b);// T 推导出是int类型
	cout << "a = " << a << "  ";
	cout << "b = " << b << endl;

	// 2、显示指定类型
	int c = 30;
	int d = 40;
	mySwap<int>(c, d);// 这里T 的数据类型就是 int
	cout << "c = " << c << "  ";
	cout << "d = " << d << endl;

	double e = 1.1;
	double f = 2.2;
	mySwap<double>(e, f);
	// swapDouble(e,f);
	cout << "e = " << e << " ";
	cout << "f = " << f << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/04e60d7b66254d4d92c3eeeb381b00ad.png)	
## 30.3 函数模板注意事项
注意事项：

* **自动类型推导**，**必须推导出一致的数据类型 T**，才可以使用

```cpp
template<class T> // typename可以替换成class
void mySwap(T& a, T& b)
{
	T temp = a;
	a = b;
	b = temp;
}

// 1、自动类型推导，必须推导出一直的数据类型T才可以使用
void test01()
{
	int a = 10;
	int b = 20;// 明确数据类型
	char c = 'c';
	mySwap(a, b);
	// mySwap(a,c); 错误，a 和 c 不是同一种类型
	cout << "a = " << a << endl;
	cout << "b = " << b << endl;
}
```
* **模板必须要确定出T的数据类型，才可以使用**

```cpp
// 2、模板必须要确定出T的类型，才可以使用
template<class T>
void func()
{
	cout << "func 调用" << endl;// 无返回值类型
}

void test02()
{
	func<int>();// 一定要加数据类型 int
}
```

 - 总程序

```cpp
#include<iostream>
using namespace std;

// 函数模板注意事项

template<class T> // typename可以替换成class
void mySwap(T& a, T& b)
{
	T temp = a;
	a = b;
	b = temp;
}

// 1、自动类型推导，必须推导出一直的数据类型T才可以使用
void test01()
{
	int a = 10;
	int b = 20;// 明确数据类型
	char c = 'c';
	mySwap(a, b);
	// mySwap(a,c); 错误，a 和 c 不是同一种类型
	cout << "a = " << a << endl;
	cout << "b = " << b << endl;
}

// 2、模板必须要确定出T的类型，才可以使用
template<class T>
void func()
{
	cout << "func 调用" << endl;// 无返回值类型
}

void test02()
{
	func<int>();// 一定要加数据类型 int
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/2646d322e920444c96644f13d3dac7cb.png)	
## 30.4 函数模板案例
案例描述：

* 利用函数模板封装一个排序的函数，可以对**不同数据类型数组**进行排序
* 排序规则从大到小，排序算法为**选择排序**
* 分别利用**char数组**和**int数组**进行测试

```cpp
#include<iostream>
using namespace std;

// 实现通用数组的排序
// 规则 从大到小
// 算法 选择排序
// 测试 char数组，int数组

// 交换函数模板
template<class T>
void mySwap(T& a, T& b)// 引用方式交换
{
	T temp = a;
	a = b;
	b = temp;
}

// 打印数组模板
template<class T>
void printArray(T arr[], int len)
{
	for (int i = 0; i < len; i++)
	{
		cout << arr[i] << " ";
	}
	cout << endl;
}

// 排序算法
template<class T>
void mySort(T arr[], int len)
{
	for (int i = 0; i < len; i++)
	{
		int max = i;// 认定最大值的下标
		for (int j = i + 1; j < len; j++)
		{
			// 认定的最大值比遍历的数值要小，说明j下标的元素才是真正的最大值
			if (arr[max] < arr[j])
			{
				max = j;// 更新最大值下标
			}
		}
		if (max != i) // 如果认定的最大值i不等于计算出来的最大值max
		{
			// 交换max和i元素
			mySwap(arr[max], arr[i]);
		}
	}
}

void test01()
{
	// 测试char数组
	char charArr[] = "bacdfe";
	int num = sizeof(charArr) / sizeof(char);
	printArray(charArr, num);
	mySort(charArr, num);
	printArray(charArr, num);
}

void test02()
{
	// 测试int数组
	int intArr[] = { 7, 5, 8, 1, 3, 9, 2, 4, 6 };
	int num = sizeof(intArr) / sizeof(int);
	printArray(intArr, num);
	mySort(intArr, num);
	printArray(intArr, num);
}

int main()
{
	test01();
	cout << endl;
	test02();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/56228b4acd354d958c90f8a94d6ec620.png)	
## 30.5 普通函数和函数模板的区别
**普通函数与函数模板区别：**

 * 普通函数调用时可以发生自动类型转换（隐式类型转换）
 * 函数模板调用时，如果利用自动类型推导，不会发生隐式类型转换
 * 如果利用显示指定类型的方式，可以发生隐式类型转换

 **总结：**
 * 建议使用显示指定类型的方式，调用函数模板，因为可以自己确定通用类型T

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
using namespace std;

// 普通模板和函数模板之间的区别

// 1. 普通函数调用可以发生隐式类型转换(自动类型转换)
// 2. 函数模板 用自动类型推导，不可以发生隐式类型转换
// 3. 函数模板 用显示指定类型，可以发生隐式类型转换

// 普通函数
int myAdd01(int a, int b)
{
	return a + b;
}

// 函数模板
template<class T>
T myAdd02(T a, T b)// 返回类型为T的值
{
	return a + b;
}

void test01()
{
	int a = 10;
	int b = 20;
	char c = 'c';// c == 99
	// 普通函数隐式类型转换
	cout << myAdd01(a, c) << endl;// 109

	// 函数模板自动类型推导
	cout << myAdd02(a, b) << endl;// 正确
	// cout << myAdd02(a, c) << endl;// 错误，a 和 c 的类型不同

	// 函数模板显示指定类型
	cout << myAdd02<int>(a, c) << endl;// 正确，显示类型可以发生转换，T = int
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/65ef73da43624de48cec1b8f2dfd76d6.png)	
## 30.6 普通函数和函数模板的调用规则
**调用规则**如下：

1. 如果函数模板和普通函数都可以实现，**优先调用普通函数**
2. 可以通过空模板参数列表来强制调用函数模板
3. 函数模板也可以发生重载
4. 如果函数模板可以产生更好的匹配,优先调用函数模板

**总结**

 - **既然提供了函数模板，最好就不要提供普通函数，否则容易出现二义性**

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
using namespace std;

// 普通模板和函数模板的调用规则
// 1. 如果函数模板和普通函数都可以实现，优先调用普通函数
// 2. 可以通过空模板参数列表来强制调用函数模板
// 3. 函数模板也可以发生重载
// 4. 如果函数模板可以产生更好的匹配,优先调用函数模板

// 普通函数 与 函数模板 调用规则
void myPrint(int a, int b)
{
	cout << "调用 普通函数" << endl;
}

template<class T>
void myPrint(T a, T b)
{
	cout << "调用 函数模板" << endl;
}

template<typename T>
void myPrint(T a, T b, T c)// 多了一个参数，相对于上面是重载
{
	cout << "调用 重载模板" << endl;
}

void test01()
{
	// 如果告诉编译器，普通函数是有的，但只是声明没有实现，或者不在当前文件内实现，就会报错找不到
	int a = 10;
	int b = 20;
	myPrint(a, b); // 调用 普通函数

	// 可以通过空模板参数列表来强制调用函数模板
	myPrint<>(a, b); // 调用 函数模板

	// 函数模板也可以发生重载
	int c = 30;
	myPrint(a, b, c); // 调用 重载函数模板

	// 如果函数模板可以产生更好的匹配, 优先调用函数模板(不用发生隐式函数转换)
	char c1 = 'a';
	char c2 = 'b';
	myPrint(c1, c2); // 调用 函数模板
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/fe57708474604ef8a3f5a382e3a2c0c9.png)	
## 30.7 模板的局限性(重点)
**局限性：**
* 模板的通用性并不是万能的

**例如：**

```C++
	template<class T>
	void f(T a, T b)
	{ 
    	a = b;
    }
```
在上述代码中提供的赋值操作，如果传入的a和b是一个数组，就无法实现了

再例如：

```C++
	template<class T>
	void f(T a, T b)
	{ 
    	if(a > b) { ... }
    }
```

在上述代码中，如果T的数据类型传入的是像Person这样的自定义数据类型，也无法正常运行。

 - 因此C++为解决这种问题，提供模板的重载，可以为这些**特定的类型**提供**具体化的模板**

总结：

* 利用具体化的模板，可以解决自定义类型的通用化
* 学习模板并不是为了写模板，而是在STL能够运用系统提供的模板

```cpp
#include<iostream>
#include <string>
using namespace std;

// 模板局限性
// 模板不是万能的，有些特定数据类型，需要用具体化方式做特殊实现

class Person
{
public:
	Person(string name, int age)
	{
		this->m_Name = name;
		this->m_Age = age;
	}
	// 姓名
	string m_Name;
	// 年龄
	int m_Age;
};

// 普通函数模板
// 对比两个数据是否相等
template<class T>
bool myCompare(T& a, T& b)
{
	if (a == b)
	{
		return true;
	}
	else
	{
		return false;
	}
}

// 具体化，显示具体化的原型和定意思以 template<> 开头，并通过名称来指出类型
// 具体化优先于常规模板
template<>bool myCompare(Person& p1, Person& p2)
{
	if (p1.m_Name == p2.m_Name && p1.m_Age == p2.m_Age)
	{
		return true;
	}
	else
	{
		return false;
	}
}

void test01()// 普通函数模板
{
	int a = 10;
	int b = 20;
	// 内置数据类型可以直接使用 通用的函数模板
	bool ret = myCompare(a, b);
	if (ret)
	{
		cout << "a == b " << endl;
	}
	else
	{
		cout << "a != b " << endl;
	}
}

void test02()// 具体化实现
{
	Person p1("Tom", 10);
	Person p2("Tom", 10);
	// 自定义数据类型，不会调用普通的函数模板
	// 可以创建具体化的Person数据类型的模板，用于特殊处理这个类型
	bool ret = myCompare(p1, p2);
	if (ret)
	{
		cout << "p1 == p2 " << endl;
	}
	else
	{
		cout << "p1 != p2 " << endl;
	}
}

int main() {

	test01();
	test02();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/751925512ccb41f1bcdeb53f1b1eb738.png)	

# 31 类模板

## 31.1 类模板语法

类模板作用：
- 建立一个通用类，类中的成员 数据类型可以不具体指定，用一个**虚拟的类型**来代表。

**语法：** 

```c++
template<typename T>
类
```
**解释：**

 - template  ---  声明创建模板
 - typename  --- 表面其后面的符号是一种数据类型，可以**用class代替**
 - T    ---   通用的数据类型，名称可以替换，通常为大写字母

 **总结**：
 类模板和函数模板语法相似，在声明模板template后面加类，此类称为类模板

```cpp
#include<iostream>
#include <string>
using namespace std;

// 类模板
template<class NameType, class AgeType>
class Person
{
public:
	Person(NameType name, AgeType age)
	{
		this->mName = name;
		this->mAge = age;
	}
	void showPerson()
	{
		cout << "name: " << this->mName << " age: " << this->mAge << endl;
	}
public:
	NameType mName;
	AgeType mAge;
};

void test01()
{
	// 指定NameType 为string类型，AgeType 为 int类型
	Person<string, int>P1("孙悟空", 999);
	P1.showPerson();
}

int main() {

	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/866af11db7724aee8c9a64a34d6eca64.png)

## 31.2 类模板与函数模板区别
类模板与函数模板**区别主要有两点**：

1. 类模板没有自动类型推导的使用方式
2. 类模板在模板参数列表中可以有默认参数

**总结**：

* 类模板使用只能用显示指定类型方式
* 类模板中的模板参数列表可以有默认参数

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
using namespace std;

// 类模板中成员函数的创建时机
// 类模板中成员函数在调用时才去创建

class Person1
{
public:
	void showPerson1()
	{
		cout << "Person1 show" << endl;
	}
};

class Person2
{
public:
	void showPerson2()
	{
		cout << "Person2 show" << endl;
	}
};

// 类模板
template<class T>
class MyClass
{
public:
	T obj;

	// 类模板中的成员函数，并不是一开始就创建的，而是在模板调用时再生成

	void fun1()
	{
		obj.showPerson1();
	}
	void fun2()
	{
		obj.showPerson2();
	}
};

void test01()
{
	MyClass<Person1> m;
	m.fun1();
	// MyClass<Person2> m;
	// m.fun2();// 编译会出错，说明函数调用才会去创建成员函数
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/269fb253c05d4a95a79d28d346c89c1c.png)

 - 总结：**类模板中的成员函数并不是一开始就创建的，在调用时才去创建**
## 31.3 类模板成员函数创建时机
类模板中成员函数和普通类中成员函数创建时机是有区别的

* 普通类中的成员函数一开始就可以创建
* 类模板中的成员函数在调用时才创建

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
using namespace std;

// 类模板中成员函数的创建时机
// 类模板中成员函数在调用时才去创建

class Person1
{
public:
	void showPerson1()
	{
		cout << "Person1 show" << endl;
	}
};

class Person2
{
public:
	void showPerson2()
	{
		cout << "Person2 show" << endl;
	}
};

// 类模板
template<class T>
class MyClass
{
public:
	T obj;

	// 类模板中的成员函数，并不是一开始就创建的，而是在模板调用时再生成

	void fun1()
	{
		obj.showPerson1();
	}
	void fun2()
	{
		obj.showPerson2();
	}
};

void test01()
{
	MyClass<Person1> m;
	m.fun1();
	// MyClass<Person2> m;
	// m.fun2();// 编译会出错，说明函数调用才会去创建成员函数
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
## 31.4 类模板对象做函数参数
**学习目标**：

* 类模板实例化出的对象，向函数传参的方式

**一共有三种传入方式**：

 - **指定传入的类型**：直接显示对象的数据类型
 - **参数模板化**：将对象中的参数变为模板进行传递
 - **整个类模板化**：将这个对象类型 模板化进行传递

 **查看类型：typeid(T1).name()**

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
#include <string>
using namespace std;

// 类模板对象做函数参数
template<class T1, class T2>
class Person
{
public:
	Person(T1 name, T2 age) 
	{
		this->m_Name = name;// name 是 string 类型
		this->m_Age = age;
	}

	void showPerson()
	{
		cout << "姓名：" << this->m_Name << " 年龄：" << this->m_Age << endl;
	}

	T1 m_Name;
	T2 m_Age;
};

// 1、指定传入类型(常用)
void printPerson1(Person<string, int>& p)// 引用方式传入
{
	p.showPerson();
}

void test01()
{
	Person <string, int >p("孙悟空", 100);// 作为实参传入函数printPerson1中
	printPerson1(p);
	cout << endl;
}

// 2、参数模板化
template <class T1, class T2> // T1 = string T2 = int
void printPerson2(Person<T1, T2>& p)
{
	p.showPerson();
	cout << "T1的类型为： " << typeid(T1).name() << endl;
	cout << "T2的类型为： " << typeid(T2).name() << endl;
}

void test02()
{
	Person <string, int >p("猪八戒", 90);
	printPerson2(p);
	cout << endl;
}

// 3、整个类模板化
template<class T>
void printPerson3(T& p)
{
	p.showPerson();
	cout << "T的类型为： " << typeid(T).name() << endl;
}

void test03()
{
	Person <string, int >p("唐僧", 30);
	printPerson3(p);
}

int main()
{
	test01();
	test02();
	test03();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/e20ea20b4d6b4c9891cedb720d29ccb3.png)
## 31.5 类模板与继承
当类模板碰到继承时，需要注意一下几点：

* **当子类继承的父类是一个类模板时，子类在声明的时候，要指定出父类中T的类型**
* **如果不指定，编译器无法给子类分配内存**
* **如果想灵活指定出父类中T的类型，子类也需变为类模板**

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
using namespace std;

// 类模板与继承
template<class T>
class Base // 类型未知
{
	T m;
};
// Base不是一个类，只是一个模板，通过类模板实例化出来的是模板类，模板类才是一种类

// class Son:public Base  
// {    }；
// 错误，C++编译需要给子类分配内存，必须知道父类中T的类型才可以向下继承
class Son :public Base<int> // 必须指定一个类型
{

};
void test01()
{
	Son s1;
}

// 如果想灵活指定父类中T类型，子类也需要变类模板
// 类模板继承类模板 ,可以用T2指定父类中的T类型
template<class T1, class T2>
class Son2 :public Base<T2>
{
public:
	Son2()
	{
		cout << "T1的数据类型为： " << typeid(T1).name() << endl;
		cout << "T2的数据类型为： " << typeid(T2).name() << endl;
	}
	T1 obj;
};

void test02()
{
	Son2<int, char> child1;
}


int main()
{
	test01();
	test02();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/25d20ca36b1a422aa4622194dda0e954.png)

 - 总结：如果父类是类模板，子类需要指定出父类中T的数据类型

## 31.6 类模板成员函数类外实现(重要)

 - 学习目标：**能够掌握类模板中的成员函数类外实现**
 - 总结：**类模板中成员函数类外实现时，需要加上模板参数列表**

```cpp
#include<iostream>
#include <string>
using namespace std;

// 类模板中成员函数类外实现
template<class T1, class T2>
class Person
{
public:
	// 构造函数类内声明
	Person(T1 name, T2 age);
	/*{
		this->m_Name = name;
		this->m_Age = age;
	}*/

	// 成员函数类内声明
	void showPerson();
	/*{
		cout << "姓名：" << this->m_Name << "年龄：" << this->m_Age << endl;
	}*/

	T1 m_Name;
	T2 m_Age;
};

// 构造函数 类模板类外实现
template<class T1, class T2>
Person<T1, T2>::Person(T1 name, T2 age)
{
	this->m_Name = name;
	this->m_Age = age;
}

// 成员函数 类外实现
template<class T1, class T2>
void Person<T1, T2>::showPerson()
{
	cout << "姓名: " << this->m_Name << " 年龄:" << this->m_Age << endl;
}

void test01()
{
	Person<string, int> p("Tom", 20);
	p.showPerson();
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/1a2466c9257a4a699cf8dba5f0fab0e4.png)
## 31.7 类模板分文件编写(重要)
**学习目标**：

* 掌握类模板成员函数分文件编写产生的问题以及解决方式

**问题**：

* 类模板中成员函数创建时机是在调用阶段,一开始不创建，导致分文件编写时链接不到

**解决**：

* 解决方式1：**直接包含.cpp源文件**
* 解决方式2：**将声明和实现写到同一个文件中，并更改后缀名为.hpp，hpp是约定的名称，并不是强制**

### 31.7.1 方式1

- 直接包含源文件#include"person.cpp"

#### 31.7.1.1 person.h 头文件
 - .h头文件中进行类的声明，有哪些成员函数

```cpp
// 防止头文件重复包含
#pragma once
#include<iostream>
#include<string>
using namespace std;

template<class T1, class T2>
class Person {
public:
	Person(T1 name, T2 age);

	void showPerson();

public:
	T1 m_Name;
	T2 m_Age;
};
```
#### 31.7.1.2 person.cpp（成员函数说明）

```cpp
#include"person.h"

// 构造函数 类外实现
template<class T1, class T2>
Person<T1, T2>::Person(T1 name, T2 age)
{
	this->m_Name = name;
	this->m_Age = age;
}

// 成员函数 类外实现
template<class T1, class T2>
void Person<T1, T2>::showPerson()
{
	cout << "姓名: " << this->m_Name << " 年龄:" << this->m_Age << endl;
}
```
#### 31.7.1.3 main.cpp
```cpp
#include<iostream>
#include"person.cpp"
using namespace std;

// 类模板分文件编写问题及解决
void test01()
{
	Person<string, int> p("Jerry", 18);
	p.showPerson();
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
### 31.7.2 方式2(常用) 

- 将.h和.cpp中的内容写到一起，将后缀名改为.hpp文件#include"person.hpp"

#### 31.7.2.1 person.hpp 函数声明和实现都在一起

```cpp
// 防止头文件重复包含
#pragma once
#include<iostream>
#include<string>
using namespace std;

// 函数声明和函数实现都在一个文件里
template<class T1, class T2>
class Person {
public:
	Person(T1 name, T2 age);

	void showPerson();

public:
	T1 m_Name;
	T2 m_Age;
};

// 构造函数 类外实现
template<class T1, class T2>
Person<T1, T2>::Person(T1 name, T2 age)
{
	this->m_Name = name;
	this->m_Age = age;
}

// 成员函数 类外实现
template<class T1, class T2>
void Person<T1, T2>::showPerson()
{
	cout << "姓名: " << this->m_Name << " 年龄:" << this->m_Age << endl;
}
```
### 7.2.2 main.cpp
```cpp
#include<iostream>
#include"person.hpp"
using namespace std;

void test01()
{
	Person<string, int> p("Jerry", 18);
	p.showPerson();
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/1b9a76ac8bb446caa9c878015a481975.png)
## 31.8 类模板和友元(难点)
学习目标：

* 掌握类模板配合友元函数的类内和类外实现

1. 全局函数类内实现 - 直接在类内声明友元即可
2. 全局函数类外实现 - 需要提前让编译器知道全局函数的存在

```cpp
#include<iostream>
#include<string>
using namespace std;

// 通过全局函数 打印Person信息

// 提前让编译器知道，全局函数类外实现
template<class T1, class T2>
class Person;

// 成员函数 类外实现
template<class T1, class T2>
void printPerson2(Person<T1, T2> p)// 函数模板的类外实现
{
	cout << "类外实现 —— 姓名：" << p.m_Name << " 年龄：" << p.m_Age << endl;
}

template<class T1, class T2>
class Person
{
	// 方式1：全局函数 类内实现
	friend void printPerson(Person<T1, T2> p)
	{
		cout << "类内实现 —— 姓名：" << p.m_Name << " 年龄：" << p.m_Age << endl;
	}

	// 通过友元类外访问类内私有权限的成员函数
	// 友元函数是非成员函数，但声明定义都可以在类中
	
	// 方式2：全局函数 类外实现 —— 只能写申明
	// 加空模板的参数列表<>
	// 如果全局函数是类外实现的话，需要让编译器提前知道这个函数的存在
	friend void printPerson2<>(Person<T1, T2> p);// 普通函数声明

public:
	Person(T1 name, T2 age)
	{
		this->m_Name = name;
		this->m_Age = age;
	}

private:
	T1 m_Name;
	T2 m_Age;
};

// 1、全局函数在类内实现
void test01()
{
	Person<string, int>p("Tom", 90);
	printPerson(p);// 加 friend
}

// 2、全局函数在类外实现
void test02()
{
	Person<string, int>p("Jerry", 80);
	printPerson2(p);
}

int main()
{
	test01();
	test02();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/e8b3bda8bc1d46418912dedfde0aa896.png)
 - 总结：**建议全局函数做类内实现**，用法简单，而且编译器可以直接识别

## 31.9 类模板案例
案例描述:  实现一个通用的数组类，要求如下：

 * 可以**对内置数据类型以及自定义数据类型的数据进行存储**
 * **将数组中的数据存储到堆区**
 * **构造函数中可以传入数组的容量**
 * 提供**对应的拷贝构造函数以及operator = 防止浅拷贝问题**
 * 提供**尾插法和尾删法对数组中的数据进行增加和删除**
 * 可以**通过下标的方式访问数组中的元素**
 * 可以**获取数组中当前元素个数和数组的容量**

### 31.9.1 myArray.hpp代码

```cpp
#pragma once
#include <iostream>
using namespace std;

template<class T>
class MyArray
{
public:
    
	//构造函数
	MyArray(int capacity)
	{
		this->m_Capacity = capacity;
		this->m_Size = 0;
		pAddress = new T[this->m_Capacity];
	}

	//拷贝构造
	MyArray(const MyArray & arr)
	{
		this->m_Capacity = arr.m_Capacity;
		this->m_Size = arr.m_Size;
		this->pAddress = new T[this->m_Capacity];
		for (int i = 0; i < this->m_Size; i++)
		{
			//如果T为对象，而且还包含指针，必须需要重载 = 操作符，因为这个等号不是 构造 而是赋值，
			// 普通类型可以直接= 但是指针类型需要深拷贝
			this->pAddress[i] = arr.pAddress[i];
		}
	}

	//重载= 操作符  防止浅拷贝问题
	MyArray& operator=(const MyArray& myarray) {

		if (this->pAddress != NULL) {
			delete[] this->pAddress;
			this->m_Capacity = 0;
			this->m_Size = 0;
		}

		this->m_Capacity = myarray.m_Capacity;
		this->m_Size = myarray.m_Size;
		this->pAddress = new T[this->m_Capacity];
		for (int i = 0; i < this->m_Size; i++) {
			this->pAddress[i] = myarray[i];
		}
		return *this;
	}

	//重载[] 操作符  arr[0]
	T& operator [](int index)
	{
		return this->pAddress[index]; //不考虑越界，用户自己去处理
	}

	//尾插法
	void Push_back(const T & val)
	{
		if (this->m_Capacity == this->m_Size)
		{
			return;
		}
		this->pAddress[this->m_Size] = val;
		this->m_Size++;
	}

	//尾删法
	void Pop_back()
	{
		if (this->m_Size == 0)
		{
			return;
		}
		this->m_Size--;
	}

	//获取数组容量
	int getCapacity()
	{
		return this->m_Capacity;
	}

	//获取数组大小
	int	getSize()
	{
		return this->m_Size;
	}


	//析构
	~MyArray()
	{
		if (this->pAddress != NULL)
		{
			delete[] this->pAddress;
			this->pAddress = NULL;
			this->m_Capacity = 0;
			this->m_Size = 0;
		}
	}

private:
	T * pAddress;  //指向一个堆空间，这个空间存储真正的数据
	int m_Capacity; //容量
	int m_Size;   // 大小
};
```
### 31.9.2 类模板案例—数组类封装.cpp
![在这里插入图片描述](https://img-blog.csdnimg.cn/82ce17cc14fd468a8f052fa808ca92e8.png)
```cpp
#include "myArray.hpp"
#include <string>

void printIntArray(MyArray<int>& arr) {
	for (int i = 0; i < arr.getSize(); i++) {
		cout << arr[i] << " ";
	}
	cout << endl;
}

//测试内置数据类型
void test01()
{
	MyArray<int> array1(10);
	for (int i = 0; i < 10; i++)
	{
		array1.Push_back(i);
	}
	cout << "array1打印输出：" << endl;
	printIntArray(array1);
	cout << "array1的大小：" << array1.getSize() << endl;
	cout << "array1的容量：" << array1.getCapacity() << endl;

	cout << "--------------------------" << endl;

	MyArray<int> array2(array1);
	array2.Pop_back();
	cout << "array2打印输出：" << endl;
	printIntArray(array2);
	cout << "array2的大小：" << array2.getSize() << endl;
	cout << "array2的容量：" << array2.getCapacity() << endl;
}

//测试自定义数据类型
class Person {
public:
	Person() {} 
		Person(string name, int age) {
		this->m_Name = name;
		this->m_Age = age;
	}
public:
	string m_Name;
	int m_Age;
};

void printPersonArray(MyArray<Person>& personArr)
{
	for (int i = 0; i < personArr.getSize(); i++) {
		cout << "姓名：" << personArr[i].m_Name << " 年龄： " << personArr[i].m_Age << endl;
	}

}

void test02()
{
	//创建数组
	MyArray<Person> pArray(10);
	Person p1("孙悟空", 30);
	Person p2("韩信", 20);
	Person p3("妲己", 18);
	Person p4("王昭君", 15);
	Person p5("赵云", 24);

	//插入数据
	pArray.Push_back(p1);
	pArray.Push_back(p2);
	pArray.Push_back(p3);
	pArray.Push_back(p4);
	pArray.Push_back(p5);

	printPersonArray(pArray);

	cout << "pArray的大小：" << pArray.getSize() << endl;
	cout << "pArray的容量：" << pArray.getCapacity() << endl;

}

int main() {

	//test01();

	test02();

	system("pause");

	return 0;
}
```

# 提高3 STL常用容器

# 32 初识STL

## 32.1 STL 诞生
* 软件界一直希望建立一种可重复利用的东西
* C++的**面向对象**和**泛型编程**思想，目的就是**复用性的提升**
* 大多情况下，数据结构和算法都未能有一套标准，导致被迫从事大量重复工作
* 为了建立**数据结构和算法的一套标准**,诞生了**STL**

## 32.2 STL基本概念
 * STL(Standard Template Library,**标准模板库**)
 * STL 从广义上分为：**容器(container) 算法(algorithm) 迭代器(iterator)**
 * **容器**和**算法**之间通过**迭代器**进行无缝连接。
 * STL 几乎所有的代码都采用了**模板类或者模板函数**

## 32.3 STL六大组件(重点讲解前4个)
STL大体分为六大组件，分别是:**容器(数据结构)、算法、迭代器、仿函数、适配器（配接器）、空间配置器**。
 * **容器**：各种**数据结构**，如vector、list、deque、set、map等，用来存放数据。
 * **算法**：各种常用的算法，如sort、find、copy、for_each等
 * **迭代器**：扮演了**容器与算法之间的胶合剂**。
 * **仿函数**：**行为类似函数**，可作为算法的某种策略。
 * **适配器**：一种用来修饰容器或者仿函数或迭代器接口的东西。
 * **空间配置器**：负责空间的配置与管理。

## 32.4 STL中容器、算法、迭代器
### 32.4.1 容器

 - **容器**：置物之所也。**STL容器**就是将运用**最广泛的一些数据结构**实现出来
 - 常用的数据结构：**数组, 链表,树, 栈, 队列, 集合, 映射表** 等

这些容器分为**序列式容器**和**关联式容器**两种:
 - ==序列式容器==：**强调值的排序，序列式容器中的每个元素均有固定的位置**
 - ==关联式容器==：**二叉树结构，各元素之间没有严格的物理上的顺序关系**

### 32.4.2 算法

 - **算法必须通过迭代器才能访问容器中的元素**
 - **算法**：问题之解法也。有限的步骤，解决逻辑或数学上的问题，我们叫做算法(Algorithms)

算法分为：**质变算法**和**非质变算法**：

 - ==质变算法==：是指**运算过程中会更改区间内的元素的内容**。例如**拷贝，替换，删除**等等
 - ==非质变算法==：是指**运算过程中不会更改区间内的元素内容**，例如**查找、计数、遍历、寻找极值**等等

### 32.4.3 迭代器(类似指针)

 - **迭代器**：容器和算法之间粘合剂
 - 提供一种方法，使之能够**依序寻访某个容器所含的各个元素，而又无需暴露该容器的内部表示方式**
 - 每个容器(每种数据结构)都有自己专属的迭代器
 - **迭代器使用非常类似于指针，初学阶段我们可以先理解迭代器为指针**

迭代器种类如下，常用的容器中迭代器种类为**双向迭代器**和**随机访问迭代器**

| 种类               | 功能                                                     | 支持运算                                |
| ------------------ | -------------------------------------------------------- | --------------------------------------- |
| 输入迭代器         | 对数据的只读访问                                         | 只读，支持++、==、！=                   |
| 输出迭代器         | 对数据的只写访问                                         | 只写，支持++                            |
| 前向迭代器         | 读写操作，并能向前推进迭代器                             | 读写，支持++、==、！=                   |
| **双向迭代器**     | 读写操作，并能向前和向后操作                             | 读写，支持++、--，                      |
| **随机访问迭代器** | 读写操作，可以以跳跃的方式访问任意数据，功能最强的迭代器 | 读写，支持++、--、[n]、-n、<、<=、>、>= |

## 32.5 容器算法迭代器初识

 - 了解STL中容器、算法、迭代器概念之后，我们利用代码感受STL的魅力。
 - STL中最常用的容器为**vector**，可以理解为**数组**，下面我们将学习如何向这个容器中插入数据、并遍历这个容器。

### 32.5.1 vector 存放内置数据类型

 - **容器**：`vector`
 - **算法**：`for_each`
 - **迭代器**： `vector<int>::iterator`、

vector 函数
 - **v.push_back：尾插数据** 
 - **v.begin：起始迭代器，指向容器中第一个元素**
 - **v.end：结束迭代器，指向容器中最后一个元素的下一个位置**
![在这里插入图片描述](https://img-blog.csdnimg.cn/d992fe083b5b4b55bff4d2127b0e6771.png)
 - 三种遍历数据的方式
```cpp
	// 第一种遍历方式 —— 指针解引用方式
	while (itBegin != itEnd)
	{
		cout << *itBegin << endl; // 迭代器相当于指针，使用*解引用方式取值
		itBegin++;
	}

	// 第二种遍历方式 —— for循环算法
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << endl;
	}

	// 第三种遍历方式 —— 利用STL提供的遍历算法for_each
	for_each(v.begin(), v.end(), MyPrint);// 利用回调的技术
```

 - 总程序

```cpp
#include<vector> // vector 容器
#include<algorithm>
#include<iostream> // 算法头文件
using namespace std;

// vector容器存放内置的数据类型
void MyPrint(int val)
{
	cout << val << " ";
}

void test01()
{
	// 创建一个vector容器，数组
	vector<int> v;	// v相当于一个数组变量，int是数据类型

	// 向容器中插入数组，push_back-尾插数据
	v.push_back(10);
	v.push_back(20);
	v.push_back(30);
	v.push_back(40);

	// 通过迭代器访问容器中的数组，迭代器相当于一个指针
	// v.begin是起始迭代器，指向容器中第一个元素
	vector<int>::iterator itBegin = v.begin();
	// v.end是结束迭代器，指向容器中最后一个元素的下一个位置
	vector<int>::iterator itEnd = v.end();

	// 第一种遍历方式 —— 指针解引用方式
	cout << "方法1：指针解引用" << endl;
	while (itBegin != itEnd)
	{
		cout << *itBegin << " "; // 迭代器相当于指针，使用*解引用方式取值
		itBegin++;
	}
	cout << endl;

	// 第二种遍历方式 —— for循环算法
	cout << "方法2：for循环" << endl;
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;

	// 第三种遍历方式 —— 利用STL提供的遍历算法for_each
	cout << "方法3：for_each遍历" << endl;
	for_each(v.begin(), v.end(), MyPrint);// 利用回调的技术
	cout << endl;
	// 回调函数是一个被作为参数传递的函数，MyPrint作为第3个参数被传入到for_each
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/1c8316d4ec7e4e619c7c8ce67766918b.png)	
### 32.5.2  vector 存放自定义数据类型
 - 学习目标：**vector中存放自定义数据类型，并打印输出**

```cpp
#include<vector>
#include<algorithm>// 算法头文件
#include<iostream>
#include<string>
using namespace std;

// vector容器中存放自定义数据类型
class Person
{
public:
	Person(string name, int age)
	{
		this->m_Name = name;
		this->m_Age = age;
	}
	string m_Name;
	int m_Age;
};

// 存放对象
void test01()
{
	vector<Person>v;

	Person p1("aaa", 10);
	Person p2("bbb", 20);
	Person p3("ccc", 30);
	Person p4("ddd", 40);
	Person p5("eee", 50);

	// 向容器中添加数据
	v.push_back(p1);
	v.push_back(p2);
	v.push_back(p3);
	v.push_back(p4);
	v.push_back(p5);

	// 遍历容器中的数据，it是个迭代器，当做指针用
	for (vector<Person>::iterator it = v.begin(); it != v.end(); it++)
	{
		// *it解引用出来的是Person数据类型，it是指针，可以使用箭头方式
		// cout << "姓名：" << (*it).m_Name << "年龄：" << (*it).m_Age << endl;
		cout << "姓名：" << it->m_Name << " 年龄：" << it->m_Age << endl;
	}
	cout << endl;
}

// 存放自定义数据类型：指针(存放的是指针)
void test02()
{
	vector<Person*>v;

	Person p1("aaa", 10);
	Person p2("bbb", 20);
	Person p3("ccc", 30);
	Person p4("ddd", 40);
	Person p5("eee", 50);

	// 向容器中添加数据的地址
	v.push_back(&p1);
	v.push_back(&p2);
	v.push_back(&p3);
	v.push_back(&p4);
	v.push_back(&p5);

	// 遍历容器 Person 类型的指针，用*it
	for (vector<Person*>::iterator it = v.begin(); it != v.end(); it++)//Person *是指针类型
	{
		// *it 解引用出来的是Person类型的指针，(*it)就是指针
		cout << "姓名：" << (*it)->m_Name << " 年龄：" << (*it)->m_Age << endl;//(*it)是个指针
	}
}

int main()
{
	test01();
	test02();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/390360f2b235487cad99e69a62bddb82.png)
### 32.5.3 vector 容器嵌套容器
 - 学习目标：**容器中嵌套容器，我们将所有数据进行遍历输出**

```cpp
#include<vector>
#include<algorithm>// 算法头文件
#include<iostream>
using namespace std;

// 容器嵌套容器
void test01()
{
	vector<vector<int>>v;

	// 创建小容器
	vector<int>v1;
	vector<int>v2;
	vector<int>v3;
	vector<int>v4;

	// 向小容器中添加数据
	for (int i = 0; i < 4; i++)
	{
		v1.push_back(i + 1);
		v2.push_back(i + 2);
		v3.push_back(i + 3);
		v4.push_back(i + 4);
	}

	// 将小容器插入到大的容器中
	v.push_back(v1);
	v.push_back(v2);
	v.push_back(v3);
	v.push_back(v4);

	// 通过大容器把所有的数据遍历一遍
	for (vector<vector<int>>::iterator it = v.begin(); it != v.end(); it++)
	{
		// (*it) 表示容器 vector<int>
		for (vector<int>::iterator vit = (*it).begin(); vit != (*it).end(); vit++)
		{
			cout << *vit << " ";
		}
		cout << endl;
	}
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/868bc269dd2c488a9303710a38fa3def.png)	

# 33 string容器
## 33.1 string基本概念

**本质**：string是C++风格的字符串，而**string本质上是一个类**。
**string和char * 区别：**

 * char * 是一个指针
 * string是一个类，类内部封装了char\*，管理这个字符串，是一个char*型的容器。

**特点：**
 - string 类内部封装了很多成员方法，例如：查找 find，拷贝 copy，删除 delete，替换 replace，插入insert。
 - string管理char*所分配的内存，不用担心复制越界和取值越界等，由类内部进行负责

## 33.2 string构造函数

构造函数原型：
* `string();`           				   创建一个空的字符串 例如: string str
*  `string(const char* s);`	       使用字符串s初始化
* `string(const string& str);`      使用一个string对象初始化另一个string对象
* `string(int n, char c);`            使用n个字符c初始化 

```cpp
#include<vector>
#include<algorithm>//算法头文件
#include<iostream>
#include<string>
using namespace std;

/*
string是C++风格的字符串，而string本质上是一个类
string和char *区别：
1、char* 是一个指针
2、string是一个类，类内部封装了char* ，管理这个字符串，是一个char* 型的容器
*/

//string构造函数
/*
string();         		无参，默认构造。创建一个空的字符串 例如: string str;
string(const char* s); 	     传入C语言的字符串构造C++字符串，使用字符串s初始化
string(const string& str);	 拷贝构造，使用一个string对象初始化另一个string对象
string(int n, char c);       使用n个字符c初始化
*/

void test01()
{
	// 默认构造
	string s1;

	// 用C语言的字符串初始化C++的string
	const char* str = "hello world";
	string s2(str);
	cout << "s2 = " << s2 << endl;

	// 拷贝构造
	string s3(s2);
	cout << "s3 = " << s3 << endl;

	// n个字符串
	string s4(10, 'a');
	cout << "s4 = " << s4 << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/f5fab24dc7a7465db98f1999f7784473.png)
 - 总结：string的多种构造方式没有可比性，灵活使用即可
## 33.3 string赋值操作
**功能描述**：
* 给string字符串进行赋值

**赋值的函数原型**：
* `string& operator=(const char* s);`            char*类型字符串 赋值给当前的字符串
* `string& operator=(const string &s);`         把字符串s赋给当前的字符串
* `string& operator=(char c);`                     字符赋值给当前的字符串
* `string& assign(const char *s);`                把字符串s赋给当前的字符串
* `string& assign(const char *s, int n);`         把字符串s的前n个字符赋给当前的字符串
* `string& assign(const string &s);`              把字符串s赋给当前字符串
* `string& assign(int n, char c);`                  用n个字符c赋给当前字符串

总结：string的赋值方式很多，`operator=`  这种方式是比较实用的

```cpp
#include<vector>
#include<algorithm>// 算法头文件
#include<iostream>
#include<string>
using namespace std;
/*
string& operator=(const char* s);           char*类型字符串 赋值给当前的字符串
string& operator=(const string& s);			把字符串s赋给当前的字符串
string& operator=(char c);                  字符赋值给当前的字符串
string& assign(const char* s);              把字符串s赋给当前字符串
string& assign(const char* s, int n);       把字符串s的前n个字符赋给当前的字符串
string& assign(const string& s);            把字符串s赋给当前字符串
string& assign(int n, char c);              用n个字符c赋给当前字符串
*/

void test01()
{
	string str1;
	str1 = "hello world";
	cout << "str1 = " << str1 << endl;

	string str2;
	str2 = str1;
	cout << "str2 = " << str2 << endl;

	string str3;// 单个字符，用得少
	str3 = 'a';
	cout << "str3 = " << str3 << endl;

	string str4;// 使用assign函数进行赋值
	str4.assign("hello world");// 把字符串s赋给当前的字符串
	cout << "str4 = " << str4 << endl;

	string str5;
	str5.assign("hello world", 5);// 拷贝前5个字符
	cout << "str5 = " << str5 << endl;

	string str6;
	str6.assign(str5);
	cout << "str6 = " << str6 << endl;

	string str7;
	str7.assign(10, 'w');// (int n, char c)n个字符c赋给当前字符串
	cout << "str7 = " << str7 << endl;//wwwwwwwww
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/e1a721d162e14f7188759a52060d0ca8.png)
## 33.4 string字符串拼接
**功能描述：**
* 实现在字符串末尾拼接字符串

**函数原型：**

* `string& operator+=(const char* str);`                   重载+=操作符
* `string& operator+=(const char c);`                      重载+=操作符
* `string& operator+=(const string& str);`                重载+=操作符
* `string& append(const char *s); `                        把字符串s连接到当前字符串结尾
* `string& append(const char *s, int n);`                 把字符串s的前n个字符连接到当前字符串结尾
* `string& append(const string &s);`                      同operator+=(const string& str)
* `string& append(const string &s, int pos, int n);`    字符串s中从pos开始的n个字符连接到字符串结尾

```cpp
#include<vector>
#include<algorithm>//算法头文件
#include<iostream>
#include<string>
using namespace std;

//字符串拼接
/*
string& operator+=(const char* str);                  重载+=操作符
string& operator+=(const char c);                     重载+=操作符
string& operator+=(const string& str);                重载+=操作符
string& append(const char* s);                        把字符串s连接到当前字符串结尾
string& append(const char* s, int n);                 把字符串s的前n个字符连接到当前字符串结尾
string& append(const string& s);                      同operator+=(const string& str)
string& append(const string& s, int pos, int n);      字符串s中从pos开始的n个字符连接到字符串结尾
*/

void test01()
{
	string str1 = "我";
	str1 += "爱玩游戏";
	cout << "str1 = " << str1 << endl;// 我爱完游戏

	str1 += ':';
	cout << "str1 = " << str1 << endl;// 我爱完游戏:

	string str2 = "LOL DNF";
	str1 += str2;
	cout << "str1 = " << str1 << endl;// 我爱完游戏:LOL DNF

	string str3 = "I";
	str3.append(" love ");
	cout << "str3 = " << str3 << endl;// I love

	str3.append("game abcde", 4);// 把前4个字符拼接到尾处
	cout << "str3 = " << str3 << endl;// I love game

	str3.append(str2);
	cout << "str3 = " << str3 << endl;// I love gameLOL DNF

	// 参数2表示从哪个位置开始截取，参数3表示截取字符的个数
	str3.append(str2, 0, 3);// 只截取到LOL
	cout << "str3 = " << str3 << endl;// I love gameLOL DNFLOL
	str3.append(str2, 4, 6);// 只截取到DNF
	cout << "str3 = " << str3 << endl;// I love gameLOL DNFLOLNDF
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/a208220e47e3434baf42257f928bef71.png)
## 33.5 string查找和替换
**功能描述：**
* 查找：查找指定字符串是否存在
* 替换：在指定的位置替换字符串

**函数原型：**
* `int find(const string& str, int pos = 0) const;`              查找str第一次出现位置,从pos开始查找
* `int find(const char* s, int pos = 0) const; `                  查找s第一次出现位置,从pos开始查找
* `int find(const char* s, int pos, int n) const; `               从pos位置查找s的前n个字符第一次位置
* `int find(const char c, int pos = 0) const; `                   查找字符c第一次出现位置
* `int rfind(const string& str, int pos = npos) const;`        查找str最后一次位置,从pos开始查找
* `int rfind(const char* s, int pos = npos) const;`            查找s最后一次出现位置,从pos开始查找
* `int rfind(const char* s, int pos, int n) const;`              从pos查找s的前n个字符最后一次位置
* `int rfind(const char c, int pos = 0) const;  `                查找字符c最后一次出现位置
* `string& replace(int pos, int n, const string& str); `       替换从pos开始n个字符为字符串str
* `string& replace(int pos, int n,const char* s); `            替换从pos开始的n个字符为字符串s

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
#include<string>
using namespace std;

//字符串的查找和替换
/*
int find(const string& str, int pos = 0) const;               查找str第一次出现位置,从pos开始查找
int find(const char* s, int pos = 0) const;                   查找s第一次出现位置,从pos开始查找
int find(const char* s, int pos, int n) const;                从pos位置查找s的前n个字符第一次位置
int find(const char c, int pos = 0) const;                    查找字符c第一次出现位置
int rfind(const string& str, int pos = npos) const;           查找str最后一次位置,从pos开始查找
int rfind(const char* s, int pos = npos) const;               查找s最后一次出现位置,从pos开始查找
int rfind(const char* s, int pos, int n) const;               从pos查找s的前n个字符最后一次位置
int rfind(const char c, int pos = 0) const;                   查找字符c最后一次出现位置
string& replace(int pos, int n, const string& str);           替换从pos开始n个字符为字符串str(c++格式)
string& replace(int pos, int n, const char* s);               替换从pos开始n个字符为字符串s(c格式)
*/

// 1.查找
void test01()
{
	string str1 = "abcdefg";
	int pos = str1.find("de");
	if (pos == -1)
	{
		cout << "未找到字符串" << endl;
	}
	else
	{
		cout << "找到字符串，pos = " << pos << endl;//pos=3 
	}

	// rfind与find的区别：rfind从右往左查找，find是从左往右查找
	pos = str1.rfind("de");
	cout << "pos = " << pos << endl;
}

// 2.替换
void test02()
{
	string str1 = "abcdefg";
	// 从pos开始n个字符为字符串str
	// 从1号位置起(从0开始算，b开始用替代)，3个字符替换为"1111"
	str1.replace(1, 3, "1111");
	cout << "str1=" << str1 << endl;
}

int main()
{
	test01();
	test02();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/8a85be43b4f7453f9a84d28a28638cff.png)
## 33.6 string字符串比较
**功能描述：**

* 字符串之间的比较

**比较方式：**

* 字符串比较是按字符的ASCII码进行对比

= 返回   0

\> 返回   1 

< 返回  -1

**函数原型：**
 * `int compare(const string &s) const; `  与字符串s比较
 * `int compare(const char *s) const;`     与字符串s比较

 * 总结：**字符串对比主要是用于比较两个字符串是否相等**，判断谁大谁小的意义并不是很大

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
#include<string>
using namespace std;

//字符串比较：根据ASCII码一个一个顺序比较

void test01()
{
	string str1 = "hello";
	string str2 = "hello";

	if (str1.compare(str2) == 0)
	{
		cout << "str1等于str2" << endl;
	}
	else if (str1.compare(str2) > 0)
	{
		cout << "str1大于str2" << endl;
	}
	else
	{
		cout << "str1小于str2" << endl;
	}
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
## 33.7 string字符存取
string中**单个字符存取方式**有两种
 * `char& operator[](int n); `     通过[]方式取字符
 * `char& at(int n);   `              通过at方法获取字符

总结
 - string字符串中单个字符存取有两种方式，利用 [ ] 或 at

```cpp
#include<vector>
#include<iostream>
#include<string>
using namespace std;

//字符存取

void test01()
{
	string str = "hello";
	cout << "str = " << str << endl;

	// 1.通过[]访问单个字符
	for (int i = 0; i < str.size(); i++)
	{
		cout << str[i] << " ";
	}
	cout << endl;

	// 2.通过at方式访问单个字符
	for (int i = 0; i < str.size(); i++)
	{
		cout << str.at(i) << " ";
	}
	cout << endl;

	// 修改单个字符
	str[0] = 'x';
	cout << "str = " << str << endl;// xello

	str.at(1) = 'x';
	cout << "str = " << str << endl;// xxllo
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/bdc777d409854cfa87be607f06897ebb.png)
## 33.8 string字符串的插入和删除
**功能描述：**

* 对string字符串进行插入和删除字符操作

**函数原型：**

* `string& insert(int pos, const char* s);  `             插入字符串
* `string& insert(int pos, const string& str); `         插入字符串
* `string& insert(int pos, int n, char c);`                在指定位置插入n个字符c
* `string& erase(int pos, int n = npos);`                删除从Pos开始的n个字符 

**总结**
 - 插入和删除的起始下标都是从0开始

```cpp
#include<vector>
#include<iostream>
#include<string>
using namespace std;

// 字符串的插入和删除
void test01()
{
	string str = "hello";

	// 插入
	str.insert(1, "111");
	cout << "插入后str = " << str << endl;// h111ello

	// 删除
	str.erase(1, 3);// 从第1个位置起，删除3个
	cout << "删除后str = " << str << endl;// hello
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/836fb6351e63408d800c7787a6145685.png)	
## 33.9 string子串
**功能描述：**
* 从字符串中获取想要的子串

**函数原型：**
* `string substr(int pos = 0, int n = npos) const;`   返回**由pos开始的n个字符组成的字符串**

```cpp
#include<vector>
#include<iostream>
#include<string>
using namespace std;

// string求子串
void test01()
{
	string str = "abcdef";
	string subStr = str.substr(1, 3);// bcd
	cout << "subStr = " << subStr << endl;
}

// 实用操作
void test02()
{
	string email = "zhangsan@sina.com";
	// 从邮件的地址中，获取用户名的信息
	int pos = email.find("@");// pos=8
	cout << "pos = " << pos << endl;

	string userName = email.substr(0, pos);// 从第0个开始，截取8个字符
	cout << "userName = " << userName << endl;
}

int main()
{
	test01();
	test02();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/1fca56b99f7e45fdba701174af7cb17f.png)
# 34 vector容器(尾插尾删)
## 34.1 vector基本概念
**功能：**

* vector数据结构和**数组非常相似**，也称为**单端数组**

**vector与普通数组区别：**

* 不同之处在于数组是静态空间，而vector可以**动态扩展**

**动态扩展：**
* 并不是在原空间之后续接新空间，而是找更大的内存空间，然后将原数据拷贝新空间，释放原空间

![在这里插入图片描述](https://img-blog.csdnimg.cn/053c2514fd1a4091afc137bc00e04989.png)
 - vector容器的迭代器是支持随机访问的迭代器
 - 尾插和尾删，常用v.begin()和v.end()。
## 34.2 vector构造函数
**功能描述：**
* 创建vector容器

**函数原型：**

* `vector<T> v; `               		     采用模板实现类实现，默认构造函数
* `vector(v.begin(), v.end());   `        将v[begin(), end())区间中的元素拷贝给本身，前闭后开
* `vector(n, elem);`                       构造函数将n个elem拷贝给本身。
* `vector(const vector &vec);`         拷贝构造函数。

```cpp
#include<vector>
#include<string>
#include<algorithm>
#include<iostream>
using namespace std;

// 打印函数
void printVector(vector<int>& v)// 地址传递
{
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

// vector容器构造，尾插尾删
void test01()
{
	// 默认构造 无参构造
	vector<int>v1;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
	}
	printVector(v1);

	// 通过区间的方式进行构造，end值取不到
	vector<int>v2(v1.begin(), v1.end());
	printVector(v2);

	// n个elem方式构造
	vector<int>v3(10, 100);// 100 100 100 100 100 100 100 100 100 100
	printVector(v3);

	// 拷贝构造
	vector<int>v4(v3);
	printVector(v4);// 100 100 100 100 100 100 100 100 100 100
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/631646cb83764e87a765e5829b8b3e70.png)
## 34.3 vector赋值操作
**功能描述：**
* 给vector容器进行赋值

**函数原型：**
* `vector& operator=(const vector &vec);`  重载等号操作符
* `assign(beg, end);`       将[beg, end)区间中的数据拷贝赋值给本身
* `assign(n, elem);`         将n个elem拷贝赋值给本身

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
#include<string>
using namespace std;

// 打印函数
void printVector(vector<int>& v)
{
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

// vector赋值
void test01()
{
	vector<int>v1;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
	}
	printVector(v1);

	// 赋值 operator = 等号赋值
	vector<int>v2;
	v2 = v1;
	printVector(v2);

	// assign将[beg, end)区间中的数据拷贝赋值给本身
	vector<int>v3;
	v3.assign(v1.begin(), v1.end());
	printVector(v3);

	// n个elem方式赋值
	vector<int>v4;
	v4.assign(10, 100);
	printVector(v4);
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/9bbedca04e234684bd17b6952ade817e.png)	
## 34.4 vector容量capacity与大小size
**功能描述：**
* 对vector容器的容量和大小操作

**函数原型：**

* `empty(); `                        判断容器是否为空
* `capacity();`                  容器的容量
* `size();`                           返回容器中元素的个数
* `resize(int num);`        重新指定容器的长度为num，若容器变长，则以默认值填充新位置。如果容器变短，则末尾超出容器长度的元素被删除
* `resize(int num, elem);`    重新指定容器的长度为num，若容器变长，则以elem值填充新位置。如果容器变短，则末尾超出容器长度的元素被删除

**总结：**
* 判断是否为空：empty
* **返回元素个数**：size
* 返回容器容量：capacity
* 重新指定大小：resize

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
#include<string>
using namespace std;

// 打印函数
void printVector(vector<int>& v)// 引用方式传递
{
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

//vector容器的容量和大小操作
void test01()
{
	vector<int>v1;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
	}
	printVector(v1);

	if (v1.empty()) // 为真代表容器为空
	{
		cout << "v1为空" << endl;
	}
	else
	{
		cout << "v1不为空" << endl;
		cout << "v1的容量为：" << v1.capacity() << endl;// capacity >= size
		cout << "v1的大小为：" << v1.size() << endl; // v1的大小为10，容量为13
	}

	// 重新指定大小
	// v1.resize(15);
	// printVector(v1);// 如果重新指定的比原来长了，默认用0填充新的位置
	v1.resize(15, 100);// 利用重载的版本，可以指定参数2为默认的填充值
	printVector(v1);

	v1.resize(5);
	printVector(v1);// 如果重新指定的比原来短了，超出部分会删除掉
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/f6352a416f4e416abc86a145f64c592e.png)
## 34.5 vector插入和删除
**功能描述：**
* 对vector容器进行插入、删除操作

**函数原型：**

* `push_back(ele);`                                     尾部插入元素ele
* `pop_back();`                                              删除最后一个元素
* `insert(const_iterator pos, ele);`  迭代器指向位置pos插入元素ele
* `insert(const_iterator pos, int count,ele);`   迭代器指向位置pos插入count个元素ele
* `erase(const_iterator pos);`                     删除迭代器指向的元素
* `erase(const_iterator start, const_iterator end);`   删除迭代器从start到end之间的元素
* `clear();`                                                       删除容器中所有元素


```cpp
#include<vector>
#include<algorithm>
#include<iostream>
#include<string>
using namespace std;

// 插入和删除
/*
push_back(ele);                            尾部插入元素ele
pop_back();                                删除最后一个元素
insert(const_iterator pos, ele); 迭代器指向位置pos插入元素ele
insert(const_iterator pos, int count, ele); 迭代器指向位置pos插入count个元素eleerase(const_iterator pos);                     
//删除迭代器指向的元素
erase(const_iterator start, const_iterator end);    删除迭代器从start到end之间的元素
clear();                                 删除容器中所有元素
*/

// 打印函数
void printVector(vector<int>& v)
{
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

void test01()
{
	vector<int>v1;
	// 尾插法
	v1.push_back(10);
	v1.push_back(20);
	v1.push_back(30);
	v1.push_back(40);
	v1.push_back(50);

	// 遍历
	printVector(v1);

	// 尾删
	v1.pop_back();
	printVector(v1);// 50被删除，10 20 30 40

	// 插入insert 第一个参数是迭代器
	v1.insert(v1.begin(), 100);
	printVector(v1);// 100 10 20 30 40

	v1.insert(v1.begin(), 2, 1000);// 在开头多了两个1000
	printVector(v1);// 1000 1000 100 10 20 30 40 

	// 删除erase 参数也是迭代器
	v1.erase(v1.begin());
	printVector(v1);// 1000 100 10 20 30 40 

	v1.erase(v1.begin(), v1.end());// 清空 同v1.clear()
	printVector(v1);
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/a3ade2a28d3e4b7f9a42ba0c6886ddd3.png)	
## 34.6 vector数据存取
**功能描述：**
* 对vector中的数据的存取操作

**函数原型：**
* `at(int idx); `     返回索引idx所指的数据
* `operator[]; `     返回索引idx所指的数据
* `front(); `          返回容器中第一个数据元素
* `back();`           返回容器中最后一个数据元素

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
#include<string>
using namespace std;

//vector容器 数据存取

void test01()
{
	vector<int>v1;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
	}

	// 利用[]方式访问数组中的元素
	cout << "[]方式访问:";
	for (int i = 0; i < 10; i++)
	{
		cout << v1[i] << " ";
	}
	cout << endl;

	// 利用at方式访问元素
	cout << "at方式访问:";
	for (int i = 0; i < 10; i++)
	{
		cout << v1.at(i) << " ";
	}
	cout << endl;

	// 获取第一个元素
	cout << "第一个元素为：" << v1.front() << endl;

	// 获取最后的一个元素为
	cout << "最后一个元素为：" << v1.back() << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/045c193942b64584bd61797a7fa846e3.png)	
## 34.7 vector互换容器
**功能描述：**
* 实现两个容器内元素进行互换

**函数原型：**
* `swap(vec);`  将vec与本身的元素互换

**总结：**
 - swap可以使两个容器互换，可以达到实用的收缩内存效果
 - 用v的大小初始化匿名对象的大小，然后互换空间，交换容器
 - vector<int>(v)表示初始化和v大小相同的匿名对象
![在这里插入图片描述](https://img-blog.csdnimg.cn/64e18fd74e1445a9a215ad0dd5a3e999.png)

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
#include<string>
using namespace std;

// vector容器互换

// 打印函数
void printVector(vector<int>& v)
{
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

// 1.基本使用
void test01()
{
	cout << "交换前： " << endl;

	vector<int>v1;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
	}
	printVector(v1);// 0 1 2 3 4 5 6 7 8 9

	vector<int>v2;
	for (int i = 10; i > 0; i--)
	{
		v2.push_back(i);// 10 9 8 7 6 5 4 3 2 1
	}
	printVector(v2);

	cout << "交换后： " << endl;
	v1.swap(v2);
	printVector(v1);// 10 9 8 7 6 5 4 3 2 1
	printVector(v2);// 0 1 2 3 4 5 6 7 8 9
}

// 2.实际用途
// 巧用swap可以收缩内存空间
void test02()
{
	vector<int>v;
	for (int i = 0; i < 100000; i++)
	{
		v.push_back(i);
	}
	cout << "v的容量为： " << v.capacity() << endl;// 138255
	cout << "v的大小为： " << v.size() << endl;// 10000

	v.resize(3);// 重新指定大小
	cout << "v的容量为： " << v.capacity() << endl;// 138255
	cout << "v的大小为： " << v.size() << endl;// 3

	// 巧用swap收缩内存, 不会浪费内存
	vector<int>(v).swap(v);// (v)：用v的大小初始化匿名对象的大小，然后互换空间
	cout << "v的容量为： " << v.capacity() << endl;// 3
	cout << "v的大小为： " << v.size() << endl;// 3
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/339e86b3bb774802ab647d60ce03eef4.png)	
## 34.8 vector预留空间
**功能描述：**
* 减少vector在动态扩展容量时的扩展次数

**函数原型：**
* `reserve(int len);` 容器预留len个元素长度，预留位置不初始化，元素不可访问
![在这里插入图片描述](https://img-blog.csdnimg.cn/eb8a927c9b9b4cc08be1c79f22d76505.png)
 - 每次分配的内存满后就会重新分配内存，p指向新分配的内存的首地址。使用reserve预留空间

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
using namespace std;

// vector预留空间
void test01()
{
	vector<int>v;
	// 利用reserve预留空间，这样就不用开辟30次空间
	v.reserve(100000);

	int num = 0;// 统计开辟内存的次数
	int* p = NULL;
	for (int i = 0; i < 10000; i++)
	{
		v.push_back(i);
		if (p != &v[0])// 如果p不等于首地址
		{
			p = &v[0];
			num++;
		}
	}
	cout << "num = " << num << endl;// 1, 分配1次内存，因为先预留了10000个内存空间
	// v 中收元素地址变化次数，就是v在内存中的分配次数。
	// 每次分配的内存满后就会重新分配内存，p指向新分配的内存的首地址
}

int main()
{
	test01();
	system("pause"); 
	return 0;
}
```
# 35 deque容器(双端队列)
## 35.1 deque基本概念
**功能：**
* 双端队列，可以对头端进行插入删除操作

**deque与vector区别：**
 * vector对于头部的插入删除效率低，数据量越大，效率越低
 * deque相对而言，对头部的插入删除速度回比vector快
 * **vector访问元素时的速度会比deque快**，这和两者内部实现有关
 * 头部尾部的插入删除快，但访问数据效率低，因为需要重新找缓存区的地址，然后再进行访问
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/bf8acfed28ef4a419a78c52462109a3c.png)

![在这里插入图片描述](https://img-blog.csdnimg.cn/f3af0c7f926c44f7a7263fa093839f2e.png)
**deque内部工作原理:**

 * deque内部有个**中控器**，维护每段缓冲区中的内容，缓冲区中存放真实数据
 * 中控器维护的是每个缓冲区的地址，使得使用deque时像一片连续的内存空间

![在这里插入图片描述](https://img-blog.csdnimg.cn/1a519a92717f46389edad32b3732e086.png)	
 - deque容器的迭代器也是支持随机访问的

## 35.2 deque构造函数(必须用const只读迭代器)
**功能描述：**
* deque容器构造

**函数原型：**
* `deque<T>` deqT;                    默认构造形式
* `deque(beg, end);`                    构造函数将[beg, end)区间中的元素拷贝给本身。
* `deque(n, elem);`                      构造函数将n个elem拷贝给本身。
* `deque(const deque &deq);`       拷贝构造函数

```cpp
#include<algorithm>
#include<iostream>
#include<deque>
using namespace std;

// deque构造函数

// 只读迭代器
void printDeque(const deque<int>& d)// const只读，引用方式传递进来
{
	for (deque<int>::const_iterator it = d.begin(); it != d.end(); it++)
	{
		// *it=100; 容器中的数据不可以修改
		cout << *it << " ";
	}
	cout << endl;
}

void test01()
{
	deque<int>d1;
	for (int i = 0; i < 10; i++)
	{
		d1.push_back(i);
	}
	printDeque(d1);

	deque<int>d2(d1.begin(), d1.end());
	printDeque(d2);

	deque<int>d3(10, 100);// 10个100
	printDeque(d3);

	deque<int>d4(d3);// 拷贝构造
	printDeque(d4);
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/d0bc5c9f055d43e2a0bb2701f35f9605.png)	
## 35.3 deque赋值操作
**功能描述：**
* 给deque容器进行赋值

**函数原型：**
* `deque& operator=(const deque &deq); `         重载等号操作符
* `assign(beg, end);`                                      将[beg, end)区间中的数据拷贝赋值给本身。
* `assign(n, elem);`                                        将n个elem拷贝赋值给本身。

```cpp
#include<algorithm>
#include<iostream>
#include<deque>
using namespace std;

// deque容器赋值操作
void printDeque(const deque<int>& d)// const只读,只读迭代器
{
	for (deque<int>::const_iterator it = d.begin(); it != d.end(); it++)
	{
		cout << *it << " ";// 不可直接做修改操作
	}
	cout << endl;
}

void test01()
{
	deque<int>d1;
	for (int i = 0; i < 10; i++)
	{
		d1.push_back(i);
	}
	printDeque(d1);

	// operator=赋值
	deque<int>d2;
	d2 = d1;
	printDeque(d2);

	// assign赋值
	deque<int>d3;
	d3.assign(d1.begin(), d1.end());
	printDeque(d3);

	// 将n个elem拷贝赋值给本身
	deque<int>(d4);
	d4.assign(10, 100);
	printDeque(d4);
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/429db38f5cf847d89ad8b1d6d72c689f.png)
## 35.4 deque大小操作
**功能描述：**
* 对deque容器的大小进行操作，**没有容量说法只有个数**

**函数原型：**
* `deque.empty();`    判断容器是否为空
* `deque.size();`       返回容器中元素的个数
* `deque.resize(num);` 重新指定容器的长度为num,若容器变长，则以默认值填充新位置。如果容器变短，则末尾超出容器长度的元素被删除
* `deque.resize(num, elem);` 重新指定容器的长度为num，若容器变长，则以elem值填充新位置。如果容器变短，则末尾超出容器长度的元素被删除

```cpp
#include<algorithm>
#include<iostream>
#include<deque>
using namespace std;

// deque容器大小操作
void printDeque(const deque<int>& d)// const只读
{
	for (deque<int>::const_iterator it = d.begin(); it != d.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

void test01()
{
	deque<int>d1;
	for (int i = 0; i < 10; i++)
	{
		d1.push_back(i);
	}
	printDeque(d1);

	if (d1.empty())// 如果容器为空，则返回真，否则返回假
	{
		cout << " d1为空" << endl;
	}
	else
	{
		cout << "d1不为空" << endl;
		cout << "d1的大小为：" << d1.size() << endl;
		// 个数就是大小，deque容器没有容量概念，可以无限放
	}

	// 重新指定大小
	// d1.resize(15);重新指定容器的长度为num,若容器变长，则以默认值填充新位置
	// deque.resize(num, elem);重新指定容器的长度为num,若容器变长，则以elem值填充新位置
    // 如果容器变短，则末尾超出容器长度的元素被删除
	d1.resize(15, 1);// 超出部分为1
	printDeque(d1);

	d1.resize(5);
	printDeque(d1);
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/d3b5fca5d4734dc38812eeb7bc6972b5.png)
## 35.5 deque插入和删除
**功能描述：**
* 向deque容器中插入和删除数据

**函数原型**
两端插入操作：
- `push_back(elem);`   在容器尾部添加一个数据
- `push_front(elem);` 在容器头部插入一个数据
- `pop_back();`  删除容器最后一个数据
- `pop_front();` 删除容器第一个数据

指定位置操作：
* `insert(pos,elem);`  在pos位置插入一个elem元素的拷贝，返回新数据的位置
* `insert(pos,n,elem);` 在pos位置插入n个elem数据，无返回值
* `insert(pos,beg,end);` 在pos位置插入[beg,end)区间的数据，无返回值
* `clear();` 清空容器的所有数据
* `erase(beg,end);`  删除[beg,end)区间的数据，返回下一个数据的位置
* `erase(pos);` 删除pos位置的数据，返回下一个数据的位置

**总结：**
* 插入和删除提供的位置是迭代器！
* 尾插   ---  push_back
* 尾删   ---  pop_back
* 头插   ---  push_front
* 头删   ---  pop_front
  
```cpp
#include<algorithm>
#include<iostream>
#include<deque>
using namespace std;

// deque插入和删除
// 打印函数
void printDeque(const deque<int>& d)// const只读
{
	for (deque<int>::const_iterator it = d.begin(); it != d.end(); it++)// 只读迭代器
	{
		cout << *it << " ";
	}
	cout << endl;
}

// 两端操作
void test01()
{
	deque<int>d1;
	// 尾插
	d1.push_back(10);
	d1.push_back(20);
	printDeque(d1);// 10 20

	// 头插
	d1.push_front(100);
	d1.push_front(200);
	printDeque(d1);// 200 100 10 20

	// 尾删
	d1.pop_back();
	printDeque(d1);// 200 100 10

	// 头删
	d1.pop_front();
	printDeque(d1);// 100 10
}

void test02()
{
	deque<int>d1;
	d1.push_back(10);
	d1.push_back(20);
	d1.push_front(100);
	d1.push_front(200);
	printDeque(d1);// 200 100 10 20

	// insert方式插入
	d1.insert(d1.begin(), 1000);
	printDeque(d1);// 1000 200 100 10 20

	d1.insert(d1.begin(), 2, 10000);
	printDeque(d1);// 10000 10000 1000 200 100 10 20

	// 按照区间进行插入
	deque<int>d2;
	d2.push_back(1);
	d2.push_back(2);
	d2.push_back(3);

	d1.insert(d1.begin(), d2.begin(), d2.end());// 在d1的begin位置插入d2
	printDeque(d1);// 1 2 3 10000 10000 1000 200 100 10 20
}

void test03()
{
	deque<int>d1;
	d1.push_back(10);
	d1.push_back(20);
	d1.push_front(100);
	d1.push_front(200);// 200 100 10 20

	// 删除
	deque<int>::iterator it = d1.begin();// 方便删除其他地方的值
	it++;
	d1.erase(it);// 删除第2个元素
	printDeque(d1);// 200 10 20; 删除100

	// 按照区间的方式删除
	d1.erase(d1.begin(), d1.end());// 本质就是清空，同clear

	// 清空
	d1.clear();
	printDeque(d1);
}

int main()
{
	test01();
	cout << endl;
	test02();
	cout << endl;
	test03();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/0c060d72cee64f58bb15e51d9786a2bc.png)
## 35.6 deque数据存取
**功能描述：**
* 对deque 中的数据的存取操作

**函数原型：**
- `at(int idx); ` 返回索引idx所指的数据
- `operator[]; ` 返回索引idx所指的数据
- `front(); ` 返回容器中第一个数据元素
- `back(); ` 返回容器中最后一个数据元素

**总结：**

- 除了用迭代器获取deque容器中元素，**[ ]和at也可以**
- front返回容器第一个元素
- back返回容器最后一个元素
```cpp
#include<iostream>
#include<deque>
using namespace std;

void test01()
{
	deque<int>d;
	d.push_back(10);// 尾插
	d.push_back(20);
	d.push_back(30);
	d.push_front(100);// 头插
	d.push_front(200);
	d.push_front(300);

	// 通过[]方式访问元素
	// 300 200 100 10 20 30 
	for (int i = 0; i < d.size(); i++)
	{
		cout << d[i] << " ";
	}
	cout << endl;

	// 通过at方式访问元素
	for (int i = 0; i < d.size(); i++)
	{
		cout << d.at(i) << " ";
	}
	cout << endl;

	cout << "第一个元素为：" << d.front() << endl;
	cout << "最后一个元素为：" << d.back() << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/7bc2afa73b374b739804b5716681b7e3.png)	
## 35.7 deque排序
**功能描述：**
* 利用算法实现对deque容器进行排序

**算法：**
* `sort(iterator beg, iterator end)`  对beg和end区间内元素进行排序

**总结：**
 - sort算法非常实用，使用时包含头文件 algorithm即可

```cpp
#include<algorithm>
#include<iostream>
#include<deque>
using namespace std;

//deque容器排序
void printDeque(const deque<int>& d)
{
	for (deque<int>::const_iterator it = d.begin(); it != d.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

void test01()
{
	deque<int>d;
	d.push_back(10);
	d.push_back(20);
	d.push_back(30);
	d.push_front(100);
	d.push_front(200);
	d.push_front(300);
	cout << "排序前：" << endl;
	printDeque(d);// 300 200 100 10 20 30

	// 排序 默认是从小到大 升序
	// 对于支持随机访问的迭代器的容器，都可以利用sort算法直接进行排序
	// vector容器也可以利用 sort进行排序
	sort(d.begin(), d.end());
	cout << "排序后：" << endl;
	printDeque(d);
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/5ea7ab9a0b3b455ab1110842b31fe0a2.png)	
# 36 案例 评委打分
## 36.1 案例描述
 - 有5名选手：选手ABCDE，10个评委分别对每一名选手打分，去除最高分，去除评委中最低分，取平均分。

## 36.2 实现步骤
1. 创建五名选手，放到vector中
2. 遍历vector容器，取出来每一个选手，执行for循环，可以把10个评分打分存到deque容器中
3. sort算法对deque容器中分数排序，去除最高和最低分
4. deque容器遍历一遍，累加总分
5. 获取平均分

```cpp
#include<iostream>
#include<vector>
#include<algorithm>
#include<deque>
#include<string>
#include<ctime>
using namespace std;

// 需求：有5名选手ABCDE，10个评委分别对每一名选手打分，去除最高分，去除评委中最低分，取平均分
/*
1. 创建五名选手，放到vector中
2. 遍历vector容器，取出来每一个选手，执行for循环，可以把10个评分打分存到deque容器中
3. sort算法对deque容器中分数排序，去除最高和最低分
4. deque容器遍历一遍，累加总分
5. 获取平均分
*/

// 创建对象—选手类
class Person
{
public:
	Person(string name, int score)
	{
		this->m_Name = name;
		this->m_Score = score;
	}
	string m_Name;// 姓名
	int m_Score; // 平均线
};

// 创建选手
void createPerson(vector<Person>& v) // 通过引用的方式传递,实参和形参可以对应修改
{
	string nameSeed = "ABCDE";
	for (int i = 0; i < 5; i++)
	{
		string name = "选手";
		name += nameSeed[i];

		int score = 0;

		Person p(name, score);

		// 将创建的person对象放入容器中
		v.push_back(p);
	}
}

// 打分
void createScore(vector<Person>& v)
{
	// 选手用it表示
	for (vector<Person>::iterator it = v.begin(); it != v.end(); it++)
	{
		// 将评委的分数放入deque中
		deque<int>d;
		for (int i = 0; i < 10; i++)
		{
			int score = rand() % 41 + 60;//60~100
			d.push_back(score);
		}

		// 排序
		sort(d.begin(), d.end());

		// 去除最高和最低分
		d.pop_back();// 尾删
		d.pop_front();// 头删

		// 取平均分
		int sum = 0;
		for (deque<int>::iterator dit = d.begin(); dit != d.end(); dit++)
		{
			// 累加每个评委分数
			sum += *dit;
		}
		int avg = sum / d.size();

		// 将平均分赋值给选手
		it->m_Score = avg;
	}
}

// 显示分数
void showScore(vector<Person>& v)
{
	for (vector<Person>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << "姓名： " << it->m_Name << " 平均分： " << it->m_Score << endl;
	}
}

int main()
{
	// 随机数种子
	srand((unsigned int)time(NULL));

	//1.创建5名选手
	vector<Person>v; // 存放选手容器,将5名
	createPerson(v);

	// 测试
	/*for (vector<Person>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << "姓名：" << (*it).m_Name << "分数：" << (*it).m_Score << endl;
	}*/

	// 2.给5名选手打分
	createScore(v);

	// 3.显示最后得分
	showScore(v);

	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/550b70fa160b4fe4a1cf7b8f3c1b2f38.png)	

# 37 stack栈容器(先进后出)
## 37.1 stack基本概念(只使用顶端元素)
 - 概念：stack是一种**先进后出**(First In Last Out,FILO)的数据结构，它只有一个出口。

![在这里插入图片描述](https://img-blog.csdnimg.cn/a5354db3c6cd4aa9867d9b02f9b9b23a.png)
 - **栈中只有顶端的元素才可以被外界使用**，因此栈不允许有遍历行为
 - 栈中进入数据称为  --- **入栈**  `push`
 - 栈中弹出数据称为  --- **出栈**  `pop`
![在这里插入图片描述](https://img-blog.csdnimg.cn/f6b3e6b7366b422da97ef80a8767b143.png)
## 37.2 stack常用接口
**功能描述：** 栈容器常用的对外接口
**构造函数：**
* `stack<T> stk;`   stack采用模板类实现， stack对象的默认构造形式
* `stack(const stack &stk);`     拷贝构造函数

**赋值操作：**
* `stack& operator=(const stack &stk);`    重载等号操作符

**数据存取：**
* `push(elem);`      向栈顶添加元素
* `pop();`              从栈顶移除第一个元素
* `top(); `              返回栈顶元素

**大小操作：**
* `empty();`           判断堆栈是否为空
* `size(); `             返回栈的大小

**总结：**
* 入栈   --- push
* 出栈   --- pop
* 返回栈顶   --- top
* 判断栈是否为空   --- empty
* 返回栈大小   --- size
```cpp
#include<algorithm>
#include<iostream>
#include<stack>
using namespace std;

// stack容器符合先进后出，不允许有遍历行为

// 栈stack容器
void test01()
{
	// 特点：符合先进后出的数据结构
	stack<int>s;

	// 入栈
	s.push(10);
	s.push(20);
	s.push(30);
	s.push(40);

	cout << "栈的大小：" << s.size() << endl;

	// 主要栈不为空，查看栈顶，并且执行出栈操作
	while (!s.empty())// 不为空
	{
		// 查看栈顶的元素
		cout << "栈顶元素为：" << s.top() << endl;

		// 出栈
		s.pop();
	}

	cout << "栈的大小：" << s.size() << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/f97c1163cbb44002a8b6a11007b9a955.png)	
# 38 queue队列容器(先进先出)
## 38.1 queue基本概念(只使用队头队尾元素)
 - 概念：Queue是一种**先进先出**(First In First Out,FIFO)的数据结构，它有两个出口
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/e73c876e6b73402c95ff1815578ed27d.png)
 - 队列容器**允许从一端新增元素，从另一端移除元素**
 - 队列中**只有队头和队尾才可以被外界使用，因此队列不允许有遍历行为**
 - 队列中进数据称为**入队**    `push`
 - 队列中出数据称为**出队**    `pop`

## 38.2 queue常用接口
**功能描述：** 栈容器常用的对外接口
**构造函数：**
- `queue<T> que;`   queue采用模板类实现，queue对象的默认构造形式
- `queue(const queue &que);`  拷贝构造函数

**赋值操作：**
- `queue& operator=(const queue &que);`  重载等号操作符

**数据存取：**
- `push(elem);` 往队尾添加元素
- `pop();` 从队头移除第一个元素
- `back();` 返回最后一个元素
- `front(); `  返回第一个元素

**大小操作：**
- `empty();`            判断堆栈是否为空
- `size(); `              返回栈的大小

**总结：**
- 入队   --- push
- 出队   --- pop
- 返回队头元素   --- front
- 返回队尾元素   --- back
- 判断队是否为空   --- empty
- 返回队列大小   --- size

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
#include<queue>
#include<string>
using namespace std;

// queue先进先出，只有队头和队尾能给外界访问，因此不允许有遍历行为

// 队列queue
class Person
{
public:
	Person(string name, int age)
	{
		this->m_Name = name;
		this->m_Age = age;
	}
	string m_Name;
	int m_Age;
};

void test01()
{
	// 创建队列
	queue<Person>q;

	// 准备数据
	Person p1("唐僧", 30);
	Person p2("孙悟空", 1000);
	Person p3("猪八戒", 900);
	Person p4("沙僧", 800);

	// 入队 
	q.push(p1);
	q.push(p2);
	q.push(p3);
	q.push(p4);

	cout << "队列的大小：" << q.size() << endl;

	// 判断只要队列不为空，查看队头，查看队尾，出队
	while (!q.empty())
	{
		// 查看队头
		cout << "队头元素——姓名： " << q.front().m_Name << "年龄： " << q.front().m_Age << endl;

		// 查看队尾
		cout << "队尾元素——姓名： " << q.back().m_Name << "年龄： " << q.back().m_Age << endl;

		// 出队,先进先出
		q.pop();
	}

	cout << "队列的大小：" << q.size() << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/c8becb05fee04b409d7459e13d716e96.png)
# 39 list链表容器
## 39.1 list基本概念
 - **功能：** 将数据进行链式存储
 - **链表**（list）是一种物理存储单元上非连续的存储结构，数据元素的逻辑顺序是通过链表中的指针链接实现的
 - **链表的组成**：链表由一系列**结点**组成
 - **结点的组成**：一个是存储数据元素的**数据域**，另一个是存储下一个结点地址的**指针域**
 - STL中的链表是一个**双向循环链表**，既指向前一个节点，又指向后一个节点

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/c9e4f6f64bf3434091f51e53d6d65426.png)
 - 由于链表的存储方式并不是连续的内存空间，因此链表list中的迭代器只支持前移和后移，属于**双向迭代器**

**list的优点：**
* 采用动态存储分配，不会造成内存浪费和溢出
* 链表执行插入和删除操作十分方便，修改指针即可，不需要移动大量元素

**list的缺点：**
 * 链表灵活，但是空间(指针域) 和 时间（遍历）额外耗费较大

 **重要性质：**

 * List有一个重要的性质，插入操作和删除操作都不会造成原有list迭代器的失效，这在vector是不成立的。

![在这里插入图片描述](https://img-blog.csdnimg.cn/413f554ed20a4497972684e79cccc347.png)
 - 遍历速度没有指针快，因为数组地址是连续的
 - 总结：STL中**List和vector是两个最常被使用的容器**，各有优缺点。

## 39.2 list构造函数
**功能描述：**
* 创建list容器

**函数原型：**
* `list<T> lst;`             list采用采用模板类实现,对象的默认构造形式
* `list(beg,end);`         构造函数将[beg, end)区间中的元素拷贝给本身
* `list(n,elem);`           构造函数将n个elem拷贝给本身
* `list(const list &lst);`   拷贝构造函数

**总结：**
 - list构造方式同其他几个STL常用容器，熟练掌握即可

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
#include<list>
using namespace std;

// list容器的构造

void printList(const list<int>& L)
{
	for (list<int>::const_iterator it = L.begin(); it != L.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

void test01()
{
	// 创建list容器
	list<int>L1;	// 默认构造

	// 添加数据
	L1.push_back(10);
	L1.push_back(20);
	L1.push_back(30);
	L1.push_back(40);

	// 遍历容器
	printList(L1);

	// 区间方式构造
	list<int>L2(L1.begin(), L1.end());// end指向最后一个元素的下一位
	printList(L2);

	// 拷贝构造
	list<int>L3(L2);
	printList(L3);

	// n个elem
	list<int>L4(10, 1000);// 10个1000
	printList(L4);
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/b8939630dd674e1d862fcc300f5bcf59.png)
## 39.3 list赋值与交换(加const)
**功能描述：**
* 给list容器进行赋值，以及交换list容器

**函数原型：**
* `assign(beg, end);`            将[beg, end)区间中的数据拷贝赋值给本身
* `assign(n, elem);`              将n个elem拷贝赋值给本身
* `list& operator=(const list &lst);`         重载等号操作符
* `swap(lst);`                       将lst与本身的元素互换

**总结：**
 - list赋值和交换操作能够灵活运用即可

```cpp
#include<algorithm>
#include<iostream>
#include<list>
using namespace std;

// list容器的赋值与交换
void printList(const list<int>& L)// 防止修改值
{
	for (list<int>::const_iterator it = L.begin(); it != L.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

// 赋值
void test01()
{
	list<int>L1;

	// 添加数据
	L1.push_back(10);
	L1.push_back(20);
	L1.push_back(30);
	L1.push_back(40);
	printList(L1);

	list<int>L2;
	L2 = L1; // operator = 赋值
	printList(L2);

	list<int>L3;
	L3.assign(L2.begin(), L2.end());
	printList(L3);

	list<int>L4;
	L4.assign(10, 100);// 10个100
	printList(L4);
}

// 交换
void test02()
{
	list<int>L1;

	// 添加数据
	L1.push_back(10);
	L1.push_back(20);
	L1.push_back(30);
	L1.push_back(40);

	list<int>L2;
	L2.assign(10, 100);

	cout << "交换前： " << endl;
	printList(L1);
	printList(L2);

	L1.swap(L2);// 交换L1和L2
	cout << "交换后： " << endl;
	printList(L1);
	printList(L2);
}

int main()
{
	test01();
	test02();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/fcab2c37424d4787a1989109c7d573d8.png)	
## 39.4 list大小操作
**功能描述：**
* 对list容器的大小进行操作

**函数原型：**
* `size(); `             返回容器中元素的个数
* `empty(); `           判断容器是否为空
* `resize(num);`   重新指定容器的长度为num，若容器变长，则以默认值填充新位置；如果容器变短，则末尾超出容器长度的元素被删除。
* `resize(num, elem); `      重新指定容器的长度为num，若容器变长，则以elem值填充新位置；如果容器变短，则末尾超出容器长度的元素被删除。

**总结：**
- 判断是否为空   --- empty
- 返回元素个数   --- size
- 重新指定个数   --- resize
```cpp
#include<iostream>
#include<list>
using namespace std;

// list容器大小操作

void printList(const list<int>& L)// const防止修改
{
	for (list<int>::const_iterator it = L.begin(); it != L.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

void test01()
{
	list<int>L1;

	L1.push_back(10);
	L1.push_back(20);
	L1.push_back(30);
	L1.push_back(40);
	printList(L1);

	// 判断容器是否为空
	if (L1.empty())// 返回1则为空
	{
		cout << "L1为空" << endl;
	}
	else
	{
		cout << "L1不为空" << endl;
		cout << "L1的元素个数：" << L1.size() << endl;
	}

	// 重新指定大小
	L1.resize(10);// 打印出来为10 20 30 40 0 0 0 0 0 0
	printList(L1);

	L1.resize(2);// 打印10 20 
	printList(L1);
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/7e5139bd1e8c4ee6852b073f31b501b5.png)	
## 39.5 list插入与删除
**功能描述：**
* 对list容器进行数据的插入和删除

**函数原型：**
* `push_back(elem);`    在容器尾部加入一个元素
* `pop_back();`     删除容器中最后一个元素
* `push_front(elem);`    在容器开头插入一个元素
* `pop_front();`    从容器开头移除第一个元素
* `insert(pos,elem);`    在pos位置插elem元素的拷贝，返回新数据的位置
* `insert(pos,n,elem);`   在pos位置插入n个elem数据，无返回值
* `insert(pos,beg,end);`   在pos位置插入[beg,end)区间的数据，无返回值
* `clear();`   移除容器的所有数据
* `erase(beg,end);`   删除[beg,end)区间的数据，返回下一个数据的位置
* `erase(pos); `  删除pos位置的数据，返回下一个数据的位置
* `remove(elem);`   删除容器中所有与elem值匹配的元素

**总结：**
* 尾插：push_back
* 尾删：pop_back
* 头插：push_front
* 头删：pop_front
* 插入：insert
* 删除：erase
* 移除：remove
* 清空：clear


```cpp
#include<iostream>
#include<list>
using namespace std;

//list容器插入和删除
/*
push_back(elem);           在容器尾部加入一个元素
pop_back();                删除容器中最后一个元素
push_front(elem);          在容器开头插入一个元素
pop_front();               从容器开头移除第一个元素
insert(pos, elem);         在pos位置插elem元素的拷贝，返回新数据的位置。
insert(pos, n, elem);      在pos位置插入n个elem数据，无返回值。
insert(pos, beg, end);     在pos位置插入[beg,end)区间的数据，无返回值。
clear();                   移除容器的所有数据
erase(beg, end);           删除[beg,end)区间的数据，返回下一个数据的位置。
erase(pos);                删除pos位置的数据，返回下一个数据的位置。
remove(elem);              删除容器中所有与elem值匹配的元素。
*/

void printList(const list<int>& L)// const防止值被修改
{
	for (list<int>::const_iterator it = L.begin(); it != L.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

void test01()
{
	list<int>L;

	// 尾插
	L.push_back(10);
	L.push_back(20);
	L.push_back(30);

	// 头插，插入-push
	L.push_front(100);
	L.push_front(200);
	L.push_front(300);

	printList(L);// 300 200 100 10 20 30

	// 尾删，删除-pop
	L.pop_back();
	printList(L);// 300 200 100 10 20

	// 头部删除
	L.pop_front();
	printList(L);// 200 100 10 20

	// insert插入
	list<int>::iterator it = L.begin();
	// L.insert(it++, 1000);// 1000 200 100 10 20
	L.insert(++it, 1000);// 200 1000 100 10 20
	printList(L);// 第一个是迭代器，往迭代器的位置插入1000

	// 删除
	it = L.begin();
	L.erase(it);// 删除第一个位置的200
	printList(L);// 1000 100 10 20
	// L.erase(++it);// 打印出来是200 100 10 20

	// 移除
	L.push_back(10000);
	L.push_back(10000);
	L.push_back(10000);
	L.push_back(10000);
	printList(L);

	L.remove(10000);// 移除所有的10000
	printList(L);

	// 清空
	L.clear();
	printList(L);
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/5fdb11bb9c4040f288418d0089b7140f.png)	
## 39.6 list数据存取
**功能描述：**
* 对list容器中数据进行存取

**函数原型：**
* `front();`     返回第一个元素
* `back();`       返回最后一个元素

**总结：**
* list容器中不可以通过[]或者at方式访问数据，因为存储空间不是连续的，且迭代器不支持随机访问
* list本质是个链表，每个数据不是用连续的线性空间存储数据，数据地址不是连续的，迭代器也是不支持随机访问，
* 返回第一个元素   --- front
* 返回最后一个元素   --- back

```cpp
#include<iostream>
#include<list>
using namespace std;

//list数据存取

void test01()
{
	list<int>L1;
	L1.push_back(10);
	L1.push_back(20);
	L1.push_back(30);
	L1.push_back(40);

	// L1[0]不可以用[]方式访问list容器中的元素
	// L1.at(0) 不可以用at方式访问list容器中的元素
	// 原因是list本质是个链表，每个数据不是用连续的线性空间存储数据，迭代器也是不支持随机访问

	cout << "第一个元素为： " << L1.front() << endl;
	cout << "最后一个元素为： " << L1.back() << endl;

	// 验证迭代器不支持随机访问
	list<int>::iterator it = L1.begin();
	it++;
	it--;// 支持双向
	// it=it+1;	// 不支持随机访问
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/b49ee387ef4f4dc1866cecd2797bd9de.png)	
## 39.7 list反转和排序
**功能描述：**
* 将容器中的元素反转，以及将容器中的数据进行排序

**函数原型：**
* `reverse();`   反转链表
* `sort();`        链表排序

**总结：**
 * 反转   --- reverse
 * 排序   --- sort （成员函数）
 * **所有不支持随机访问迭代器的容器，不可以用标准的算法**
 * 不支持随机访问迭代器的容器，内部会提供对应的一些算法

```cpp
#include<iostream>
#include<list>
using namespace std;

// list容器反转和排序
void printList(const list<int>& L)// 打印函数
{
	for (list<int>::const_iterator it = L.begin(); it != L.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

// 反转
void test01()
{
	list<int>L1;

	L1.push_back(20);
	L1.push_back(10);
	L1.push_back(50);
	L1.push_back(40);
	L1.push_back(30);
	cout << "反转前： " << endl;
	printList(L1);

	// 反转
	L1.reverse();
	cout << "反转后： " << endl;
	printList(L1);
}

// 降序函数
bool myCompare(int v1, int v2)
{
	// 降序 就让第一个数>第二个数
	return v1 > v2;
}

// 排序
void test02()
{
	list<int>L1;

	L1.push_back(20);
	L1.push_back(10);
	L1.push_back(50);
	L1.push_back(40);
	L1.push_back(30);

	// 排序
	cout << "排序前： " << endl;
	printList(L1);

	// 所有不支持随机访问迭代器的容器，不可以用标准的算法
	// 不支持随机访问迭代器的容器，内部会提供对应的一些算法
	// sort(L1.begin(), L1.end());不能使用全局的标准算法

	L1.sort();// 要使用成员函数的算法，默认的排序规则是升序排列，排序sort调用时必须是成员函数
	cout << "升序排序后： " << endl;
	printList(L1);

	L1.sort(myCompare);
	cout << "降序排序后： " << endl;
	printList(L1);
}

int main()
{
	test01();
	test02();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/31c2b101b9fc4b8daa6f9daead1a55b5.png)	
## 39.8 list排序案例
 - 案例描述：将Person自定义数据类型进行排序，Person中属性有姓名、年龄、身高
 - 排序规则：按照年龄进行升序，如果年龄相同按照身高进行降序

```cpp
#include<iostream>
#include<list>
#include<string>
using namespace std;

class Person
{
public:
	Person(string name, int age, int height)
	{
		this->m_Name = name;
		this->m_Age = age;
		this->m_Height = height;
	}
	string m_Name;// 姓名
	int m_Age;// 年龄
	int m_Height;// 身高
};

// 指定排序规则，返回的是bool类型的数据
bool comparePerson(Person &p1,Person &p2)
{
	// 要求：首先按照年龄做升序，然后年龄相同下做身高的降序排序
	if (p1.m_Age == p2.m_Age)
	{
		// 年龄相同下做身高的降序排序
		return p1.m_Height > p2.m_Height;
	}
	else
	{
		return p1.m_Age < p2.m_Age;
	}
}

void test01()
{
	list<Person>L;// 创建容器

	// 准备数据
	Person p1("刘备", 35, 175);
	Person p2("曹操", 45, 180);
	Person p3("孙权", 40, 170);
	Person p4("赵云", 25, 190);
	Person p5("张飞", 35, 160);
	Person p6("关羽", 35, 200);

	// 插入数据
	L.push_back(p1);
	L.push_back(p2);
	L.push_back(p3);
	L.push_back(p4);
	L.push_back(p5);
	L.push_back(p6);

	cout << "排序前：" << endl;
	for (list<Person>::iterator it = L.begin(); it != L.end(); it++)
	{
		cout << "姓名： " << (*it).m_Name << " 年龄： " << it->m_Age << " 身高： " << it->m_Height << endl;
	}

	// 排序后
	cout << "----------------------------------" << endl;
	cout << "排序后：" << endl;

	L.sort(comparePerson);// 必须写一个回调函数或者仿函数，指定排序规则
	for (list<Person>::iterator it = L.begin(); it != L.end(); it++)
	{
		cout << "姓名： " << (*it).m_Name << " 年龄： " << it->m_Age << " 身高： " << it->m_Height << endl;
	}
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/033039a7388b435c814c4db15136d0ed.png)

# 40 set/multiset容器

## 40.1 set基本概念
**简介：**
* 所有元素都会在插入时自动被排序

**本质：**
* set/multiset属于**关联式容器**，底层结构是用**二叉树**实现。

**set和multiset区别**：
* set不允许容器中有重复的元素
* multiset允许容器中有重复的元素

## 40.2 set构造和赋值
**功能描述：**
 - 创建set容器以及赋值

**构造：**
* `set<T> st;`                  默认构造函数
* `set(const set &st);`       拷贝构造函数

**赋值：**
* `set& operator=(const set &st);`    重载等号操作符

**总结：**

* set容器插入数据时用insert
* set容器插入数据的数据会自动排序

```cpp
#include<iostream>
#include<set>
using namespace std;

// set容器构造与赋值操作
// 遍历
void printSet(set<int>& s)
{
	for (set<int>::iterator it = s.begin(); it != s.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

void test01()
{
	set<int>s1;

	// 插数据只有insert方式
	s1.insert(10);
	s1.insert(40);
	s1.insert(30);
	s1.insert(20);
	s1.insert(30);

	// 遍历容器
	// set容器特点：所有的元素插入的时候自动排序
	// set容器不允许插入重复值
	printSet(s1);// 10 20 30 40

	// 拷贝构造
	set<int>s2(s1);
	printSet(s2);// 10 20 30 40

	// 赋值
	set<int>s3;
	s3 = s2;
	printSet(s3);// 10 20 30 40
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
## 40.3 set大小和交换
**功能描述：**
* 统计set容器大小以及交换set容器

**函数原型：**
* `size();`           返回容器中元素的数目
* `empty();`         判断容器是否为空
* `swap(st);`       交换两个集合容器

**总结：**
* 统计大小   --- size
* 判断是否为空   --- empty
* 交换容器   --- swap

```cpp
#include<iostream>
#include<set>
using namespace std;

// set容器 大小和交换
void printSet(set<int>& s)
{
	for (set<int>::iterator it = s.begin(); it != s.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

// 大小
void test01()
{
	// 只能用insert插入数据
	set<int>s1;
	s1.insert(10);
	s1.insert(30);
	s1.insert(20);
	s1.insert(40);
	printSet(s1);// 打印容器

	// 判断是否为空
	if (s1.empty())
	{
		cout << "s1为空" << endl;
	}
	else
	{
		cout << "s1不为空" << endl;
		cout << "s1的大小为：" << s1.size() << endl;
	}
}

// 交换
void test02()
{
	// s2插入数据
	set<int>s2;
	s2.insert(10);
	s2.insert(30);
	s2.insert(20);
	s2.insert(40);

	// s3插入数据
	set<int>s3;
	s3.insert(100);
	s3.insert(300);
	s3.insert(200);
	s3.insert(400);

	cout << "交换前：" << endl;
	printSet(s2);
	printSet(s3);

	cout << "交换后：" << endl;
	s2.swap(s3);
	printSet(s2);
	printSet(s3);
}

int main()
{
	test01();
	test02();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/6bea3536712e4cdaa1ef9f889bdecbd8.png)	
## 40.4 set插入和删除
**功能描述：**
* set容器进行插入数据和删除数据

**函数原型：**
* `insert(elem);`           在容器中插入元素。
* `clear();`                  清除所有元素
* `erase(pos);`            删除pos迭代器所指的元素，返回下一个元素的迭代器。
* `erase(beg, end);`     删除区间[beg,end)的所有元素 ，返回下一个元素的迭代器。
* `erase(elem);`          删除容器中值为elem的元素。

**总结：**
* 插入   --- insert
* 删除   --- erase
* 清空   --- clear

```cpp
#include<iostream>
#include<set>
using namespace std;

// set容器的插入和删除
void printSet(set<int>& s)
{
	for (set<int>::iterator it = s.begin(); it != s.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

void test01()
{
	// s1插入数据
	set<int>s1;
	s1.insert(10);
	s1.insert(30);
	s1.insert(20);
	s1.insert(40);
	printSet(s1);// 遍历 10 20 30 40

	// 删除
	s1.erase(s1.begin());
	printSet(s1);// 20 30 40 插入后都会被排序

	// 删除的重载版本
	s1.erase(30);// 迭代器版本
	printSet(s1);// 20 40

	// 清空
	// s1.erase(s1.begin(), s1.end());
	s1.clear();
	printSet(s1);
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/d483b90f4de449e68a0858da15629137.png)
## 40.5 set查找和统计
**功能描述：**
* 对set容器进行查找数据以及统计数据

**函数原型：**
* `find(key);`   查找key是否存在，若存在，返回该键的元素的迭代器；若不存在，返回set.end()
* `count(key);`     统计key的元素个数

**总结：**
* 查找   ---  find    （返回的是迭代器）
* 统计   ---  count  （对于set，结果为0或者1）
```cpp
#include<iostream>
#include<set>
using namespace std;

// 查找
void test01()
{
	// s1插入数据
	set<int>s1;
	s1.insert(10);
	s1.insert(30);
	s1.insert(20);
	s1.insert(40);

	set<int>::iterator pos = s1.find(30);// 查找

	if (pos != s1.end())
	{
		cout << "找到元素：" << *pos << endl;// 找到迭代器的位置
	}
	else
	{
		cout << "未找到元素" << endl;
	}
}

// 统计
void test02()
{
	set<int>s2;

	// 插入数据
	s2.insert(10);
	s2.insert(30);
	s2.insert(20);
	s2.insert(40);
	s2.insert(30);
	s2.insert(30);

	// 统计30 的个数
	int num = s2.count(30);
	// 对于set而言 统计的结果要么是0，要么是1，对于重复的数只算一次。
	cout << "num = " << num << endl;
}

int main()
{
	test01();
	test02();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/48f9ca5ab29a480a89cf1298edcd4688.png)	
## 40.6 set与multiset区别
**学习目标：**
* 掌握set和multiset的区别

**区别：**
* **set不可以插入重复数据，而multiset可以**
* set插入数据的同时会返回插入结果，表示插入是否成功
* multiset不会检测数据，因此可以插入重复数据

**总结：**
* 如果不允许插入重复数据可以利用set
* 如果需要插入重复数据利用multiset

```cpp
#include<iostream>
#include<set>
using namespace std;

// set容器和multiset容器的区别
void test01()
{
	set<int>s;
	// pair为对组，iterator为迭代器，bool为布尔函数
	pair<set<int>::iterator, bool> ret = s.insert(10);

	if (ret.second){ // 主要看bool，ret第2个数据
		cout << "第一次插入成功" << endl;
	}
	else{
		cout << "第一次插入失败" << endl;
	}

	ret = s.insert(10);

	if (ret.second)
	{
		cout << "第二次插入成功" << endl;
	}
	else
	{
		cout << "第二次插入失败" << endl;
	}

	multiset<int>ms;
	// 允许插入重复值
	ms.insert(10);
	ms.insert(10);

	for (multiset<int>::iterator it = ms.begin(); it != ms.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/c86d461fb24b462195c71329431b3ba3.png)	
## 40.7 pair对组创建
**功能描述：**
* 成对出现的数据，利用对组可以返回两个数据

**两种创建方式：**
* `pair<type, type> p (value1, value2);`
* `pair<type, type> p = make_pair( value1, value2 );`

```cpp
#include<vector>
#include<algorithm>//算法头文件
#include<iostream>
#include<string>
using namespace std;

// pair对组的创建
void test01()
{
	// 第一种方式
	pair<string, int>p1("Tom", 20);
	cout << "姓名" << p1.first << "年龄：" << p1.second << endl;

	// 第二种方式
	pair<string, int>p2 = make_pair("Jerry", 30);
	cout << "姓名" << p2.first << "年龄：" << p2.second << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/28e4dd322a85449d83ce254c1d79e94d.png)	
## 40.8 set容器排序
**学习目标：**
* **set容器默认排序规则为从小到大**，掌握如何改变排序规则

**主要技术点：**
* 利用仿函数，可以改变排序规则

### 40.8.1 内置类型指定排序

 - 报错的话，在仿函数参数列表后面加const：**bool operator()(int v1,int v2)const**
```cpp
#include<iostream>
#include<set>
using namespace std;
// set容器排序

// 仿函数形式写从大到小的排列
// 仿函数是bool类型
class MyCompare
{
public:
	bool operator()(int v1,int v2)const // 第一个()表示重载的符号，第二个()表示函数的参数列表
	{
		return v1 > v2;// 做降序排列，当第一个数大于第二个数的时候，return真，否则return假
	}
};

void test01()
{
	set<int>s1;
	s1.insert(10);
	s1.insert(40);
	s1.insert(20);
	s1.insert(50);
	s1.insert(30);

	// 打印函数
	for (set<int>::iterator it = s1.begin(); it != s1.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;

	// 指定排序规则为从大到小
	set<int, MyCompare>s2;// 把仿函数放到第二个位置，仿函数做从大到小排序
	s2.insert(10);
	s2.insert(40);
	s2.insert(20);
	s2.insert(50);
	s2.insert(30);

	for (set<int, MyCompare>::iterator it = s2.begin(); it != s2.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/9cee376ed4004a719f2869bb9b12b8cc.png)	
### 40.8.2 自定义数据类型指定排序
 - 自定义数据类型，都会指定排序规则，不指定排序规则的话会报错

```cpp
#include<iostream>
#include<set>
#include<string>
using namespace std;

// set容器排序，存放自定义数据类型
class Person
{
public:
	Person(string name, int age)
	{
		this->m_Name = name;
		this->m_Age = age;
	}
	string m_Name;
	int m_Age;
};

// 写仿函数指定排序规则 仿函数本质是类，返回bool类型
class comparePerson
{
public:
	// 引用方式做传递，加const不能修改
	bool operator()(const Person& p1, const Person& p2)const// 最后一定要加const
	{
		// 按照年龄降序
		return p1.m_Age > p2.m_Age;
	}
};

void test01()
{
	// 自定义数据类型，都会指定排序规则，不指定排序规则的话会报错
	set<Person,comparePerson>s;

	// 创建Person对象
	Person p1("刘备", 24);
	Person p2("关羽", 28);
	Person p3("张飞", 25);
	Person p4("赵云", 21);

	s.insert(p1);
	s.insert(p2);
	s.insert(p3);
	s.insert(p4);

	for (set<Person,comparePerson>::iterator it = s.begin(); it != s.end(); it++)
	{
		cout << "姓名: " << it->m_Name << " 年龄：" << it->m_Age << endl;
	}
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/f7755c0aa1b1447e9bbfd2b931948477.png)
# 41 map/multimap容器
## 41.1 map基本概念
**简介：**
* **map中所有元素都是pair**
* **pair中第一个元素为key(键值)，起到索引作用，第二个元素为value(实值)**
* 所有元素都会根据元素的键值自动排序

**本质：**
* map/multimap属于**关联式容器**，底层结构是用二叉树实现

**优点：**
* 可以根据key值快速找到value值

**map和multimap区别：**
- map不允许容器中有重复key值元素
- multimap允许容器中有重复key值元素

## 41.2 map构造和赋值
**功能描述：**
* 对map容器进行构造和赋值操作

**函数原型：**

**构造：**
* `map<T1, T2> mp;`           map默认构造函数
* `map(const map &mp);`   拷贝构造函数

**赋值：**
* `map& operator=(const map &mp);`    重载等号操作符

**总结：**
 - map中所有元素都是成对出现，插入数据时候要使用对组

```cpp
#include<iostream>
#include<map>
using namespace std;

// map容器 构造和赋值，map中元素都是pair

// 打印容器
void printMap(map<int, int>& m)
{
	for (map<int, int>::iterator it = m.begin(); it != m.end(); it++)
	{
		cout << "key = " << (*it).first << " value = " << it->second << endl;
	}
	cout << endl;
}

void test01()
{
	// 创建map容器
	map<int, int>m;// 第一个是key值，第二个是value值
	// 匿名的对组放入到容器中，1起到索引作用，10是实值
	m.insert(pair<int, int>(1, 10));
	m.insert(pair<int, int>(2, 20));
	m.insert(pair<int, int>(3, 30));
	m.insert(pair<int, int>(4, 40));
	printMap(m);

	// 拷贝构造
	map<int, int>m2(m);
	printMap(m2);

	// 赋值
	map<int, int>m3;
	m3 = m2;
	printMap(m3);
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/5489dbd12715452eba1ae960e52586f4.png)	
## 41.3 map大小和交换
**功能描述：**
* 统计map容器大小以及交换map容器

**函数原型：**
- `size();`        返回容器中元素的数目
- `empty();`      判断容器是否为空
- `swap(st);`    交换两个集合容器

```cpp
#include<iostream>
#include<map>
using namespace std;

// map容器大小和交换

// 打印容器
void printMap(map<int, int>& m)
{
	for (map<int, int>::iterator it = m.begin(); it != m.end(); it++)
	{
		cout << "key = " << (*it).first << " value = " << it->second << endl;
	}
	cout << endl;
}

// 大小
void test01()
{
	map<int, int>m;
	m.insert(pair<int, int>(1, 10));
	m.insert(pair<int, int>(2, 20));
	m.insert(pair<int, int>(3, 30));
	m.insert(pair<int, int>(4, 40));

	if (m.empty())
	{
		cout << "m为空" << endl;
	}
	else
	{
		cout << "m不为空" << endl;
		cout << "m的大小为：" << m.size() << endl;
	}
}

// 交换
void test02()
{
	map<int, int>m1;
	m1.insert(pair<int, int>(1, 10));
	m1.insert(pair<int, int>(2, 20));
	m1.insert(pair<int, int>(3, 30));
	m1.insert(pair<int, int>(4, 40));

	map<int, int>m2;
	m2.insert(pair<int, int>(5, 50));
	m2.insert(pair<int, int>(6, 60));
	m2.insert(pair<int, int>(7, 70));
	m2.insert(pair<int, int>(8, 80));

	cout << "交换前：" << endl;
	printMap(m1);
	printMap(m2);

	m1.swap(m2);//m1和m2交换
	cout << "交换后：" << endl;
	printMap(m1);
	printMap(m2);
}

int main()
{
	test01();
	test02();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/d68003e1f62b4832a5c57e37caa3668a.png)	
## 41.4 map插入和删除
**功能描述：**
- map容器进行插入数据和删除数据

**函数原型：**
- `insert(elem);`            在容器中插入元素。
- `make_pair()`             插入元素(建议使用)
- `clear();`                   清除所有元素
- `erase(pos);`             删除pos迭代器所指的元素，返回下一个元素的迭代器。
- `erase(beg, end);`      删除区间[beg,end)的所有元素 ，返回下一个元素的迭代器。
- `erase(key);`             删除容器中值为key的元素。

**总结：**
* map插入方式很多，记住其一即可
- 插入：insert 
- 删除：erase
- 清空：clear
```cpp
#include<iostream>
#include<map>
using namespace std;

// map容器插入和删除
void printMap(map<int, int>& m)// 打印函数
{
	for (map<int, int>::iterator it = m.begin(); it != m.end(); it++)
	{
		cout << "key = " << it->first << " value = " << it->second << endl;
	}
	cout << endl;
}

void test01()
{
	// 插入
	map<int, int>m;

	// 第一种
	m.insert(pair<int, int>(1, 10));

	// 第二种(建议)
	m.insert(make_pair(2, 20));

	// 第三种(不建议使用)
	m.insert(map<int, int>::value_type(3, 30));

	// 第四种(不建议使用)
	m[4] = 40;

	// []不建议插入，用途 可以利用key访问到value
	printMap(m);

	// 删除
	m.erase(m.begin());
	printMap(m);

	m.erase(3);// 按照key删除
	printMap(m);

	// 清空
	m.erase(m.begin(), m.end());
	// m.clear();
	printMap(m);
}

int main()
{
	test01();
	system("pause"); 
	return 0;
}
```
## 41.5 map查找和统计
**功能描述：**
- 对map容器进行查找数据以及统计数据

**函数原型：**
- `find(key);`          查找key是否存在,若存在，返回该键的元素的迭代器；若不存在，返回set.end();
- `count(key);`        统计key的元素个数

```cpp
#include<iostream>
#include<map>
using namespace std;

// map容器 查找和统计，根据key值进行统计和查找
void test01()
{
	map<int, int>m;
	m.insert(pair<int, int>(1, 10));
	m.insert(pair<int, int>(2, 20));
	m.insert(pair<int, int>(3, 30));

	map<int, int>::iterator pos = m.find(3);// 找key=3,返回的是迭代器。无论是否找到都返回迭代器

	if (pos != m.end())// 迭代器的位置是否为end，迭代器可以理解为是指针
	{
		cout << "查到了元素 key = " << (*pos).first << " value = " << pos->second << endl;
	}
	else
	{
		cout << "未找到元素" << endl;
	}

	// 统计
	// map不允许插入重复key元素，count统计而言，结果要么是1，要么是0
	// multimap的count统计可能大于1
	int num = m.count(3);
	cout << "num = " << num << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/91adda0ecc0a4ae298cea423d7700290.png)	
## 41.6 map排序
**学习目标：**
- map容器默认排序规则为 按照key值进行 从小到大排序，掌握如何改变排序规则

**主要技术点:**
- 利用仿函数，可以改变排序规则

```cpp
#include<iostream>
#include<map>
using namespace std;

// 仿函数
class MyCompare
{
public:
	bool operator()(int v1, int v2)const // 最后一定要加 const
	{
		// 降序
		return v1 > v2;// 第一个数字大于第二个数字为真，否则为假
	}
};

void test01()
{
	map<int, int, MyCompare>m;// 默认的是从小到大排序
	// 等同于pair<int,int>(1,10)，第1个数字是key值
	m.insert(make_pair(1, 10));
	m.insert(make_pair(2, 20));
	m.insert(make_pair(3, 30));
	m.insert(make_pair(4, 40));
	m.insert(make_pair(5, 50));

	for (map<int, int, MyCompare>::iterator it = m.begin(); it != m.end(); it++)
	{
		cout << "key = " << it->first << " value = " << (*it).second << endl;
	}
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/828fd9761fdd4340885a30c9475dcaf5.png)
# 42 案例 员工分组
## 42.1 案例描述
* 公司今天招聘了10个员工（ABCDEFGHIJ），10名员工进入公司之后，需要指派员工在那个部门工作
* 员工信息有: 姓名  工资组成；部门分为：策划、美术、研发
* 随机给10名员工分配部门和工资
* 通过multimap进行信息的插入  key(部门编号) value(员工)
* 分部门显示员工信息

## 42.2 实现步骤
1. 创建10名员工，放到vector中
2. 遍历vector容器，取出每个员工，进行随机分组
3. 分组后，将员工部门编号作为key，具体员工作为value，放入到multimap容器中
4. 分部门显示员工信息

```cpp
#include<iostream>
#include <vector>
#include <string>
#include <map>
#include <ctime>
using namespace std;
/*
- 公司今天招聘了10个员工（ABCDEFGHIJ），10名员工进入公司之后，需要指派员工在那个部门工作
- 员工信息有: 姓名  工资组成；部门分为：策划、美术、研发
- 随机给10名员工分配部门和工资
- 通过multimap进行信息的插入  key(部门编号) value(员工)
- 分部门显示员工信息
*/

#define CEHUA  0
#define MEISHU 1
#define YANFA  2

class Worker
{
public:
	string m_Name;
	int m_Salary;
};

void createWorker(vector<Worker>&v)
{
	string nameSeed = "ABCDEFGHIJ";
	for (int i = 0; i < 10; i++)
	{
		Worker worker;
		worker.m_Name = "员工";
		worker.m_Name += nameSeed[i];

		worker.m_Salary = rand() % 10000 + 10000; // 10000 ~ 19999
		// 将员工放入到容器中
		v.push_back(worker);
	}
}

// 员工分组
void setGroup(vector<Worker>&v,multimap<int,Worker>&m)
{
	for (vector<Worker>::iterator it = v.begin(); it != v.end(); it++)
	{
		// 产生随机部门编号
		int deptId = rand() % 3; // 0 1 2 

		// 将员工插入到分组中
		// key部门编号，value具体员工
		m.insert(make_pair(deptId, *it));
	}
}

void showWorkerByGourp(multimap<int,Worker>&m)
{
	// 0  A  B  C   1  D  E   2  F G ...
	cout << "策划部门：" << endl;

	multimap<int,Worker>::iterator pos = m.find(CEHUA);
	int count = m.count(CEHUA); // 统计具体人数
	int index = 0;
	for (; pos != m.end() && index < count; pos++ , index++)
	{
		cout << "姓名： " << pos->second.m_Name << " 工资： " << pos->second.m_Salary << endl;
	}

	cout << "----------------------" << endl;
	cout << "美术部门： " << endl;
	pos = m.find(MEISHU);
	count = m.count(MEISHU); // 统计具体人数
	index = 0;
	for (; pos != m.end() && index < count; pos++, index++)
	{
		cout << "姓名： " << pos->second.m_Name << " 工资： " << pos->second.m_Salary << endl;
	}

	cout << "----------------------" << endl;
	cout << "研发部门： " << endl;
	pos = m.find(YANFA);
	count = m.count(YANFA); // 统计具体人数
	index = 0;
	for (; pos != m.end() && index < count; pos++, index++)
	{
		cout << "姓名： " << pos->second.m_Name << " 工资： " << pos->second.m_Salary << endl;
	}

}

int main() {

	srand((unsigned int)time(NULL));

	// 1、创建员工
	vector<Worker>vWorker;
	createWorker(vWorker);

	// 2、员工分组
	multimap<int, Worker>mWorker;
	setGroup(vWorker, mWorker);

	// 3、分组显示员工
	showWorkerByGourp(mWorker);
	system("pause");
	return 0;
}
```

# 提高4 STL函数对象

# 43 函数对象
## 43.1 函数对象概念
**概念：**
* 重载**函数调用操作符**的类，其对象常称为**函数对象**
* **函数对象**使用重载的()时，行为类似函数调用，也叫**仿函数**

**本质：**
 - 函数对象(仿函数)是一个**类**，不是一个函数

## 43.2 函数对象使用
**特点：**
* 函数对象在使用时，可以像普通函数那样调用, 可以有参数，可以有返回值
* 函数对象超出普通函数的概念，函数对象可以有自己的状态
* 函数对象可以作为参数传递

**总结：**
* 仿函数写法非常灵活，可以作为参数进行传递。

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
#include <string>
using namespace std;

// 函数对象（仿函数）

/*
函数对象在使用时，可以像普通函数那样调用, 可以有参数，可以有返回值
函数对象超出普通函数的概念，函数对象可以有自己的状态
函数对象可以作为参数传递
*/

// 1、函数对象在使用时，可以像普通函数那样调用, 可以有参数，可以有返回值
class MyAdd
{
public:
	int operator()(int v1, int v2)const
	{
		return v1 + v2;
	}
};

void test01()
{
	MyAdd myAdd;
	cout << myAdd(10, 10) << endl;
}

// 2、函数对象超出普通函数的概念，函数对象可以有自己的状态
class MyPrint
{
public:
	MyPrint()
	{
		this->count = 0;
	}
	void operator()(string test)
	{
		cout << test << endl;
		count++; // 统计使用次数
	}

	int count; // 内部自己的状态
};

void test02()
{
	MyPrint myPrint;
	myPrint("hello world");
	myPrint("hello world");
	myPrint("hello world");
	cout << "myPrint调用次数为： " << myPrint.count << endl;
}

// 3、函数对象可以作为参数传递
void doPrint(MyPrint& mp, string test)
{
	mp(test);
}

void test03()
{
	MyPrint myPrint;
	doPrint(myPrint, "Hello C++");
}

int main() {

	test01();
	cout << endl;
	test02();
	cout << endl;
	test03();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/bf24f3e7b0af4f6fa2d92b7826f33b07.png)
# 44 谓词
## 44.1 谓词概念
**概念：**
* **返回bool类型的仿函数**称为**谓词**
* 如果operator()接受一个参数，那么叫做一元谓词
* 如果operator()接受两个参数，那么叫做二元谓词

##  44.2 一元谓词
 - **总结：**参数只有一个的谓词，称为一元谓词

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
#include<vector>
using namespace std;

// 仿函数 返回值类型是bool类型，称为谓词
// 一元谓词

class GreaterFive
{
public:
	bool operator()(int val)// 返回bool类型的仿函数称为谓词
	{
		return val > 5;
	}
};

void test01()
{
	vector<int>v;
	for (int i = 0; i < 5; i++)
	{
		v.push_back(i);
	}

	// 查找容器中 有没有大于5的数字
	// GreaterFive()匿名函数对象，Pred表示想要谓词
	vector<int>::iterator it = find_if(v.begin(), v.end(), GreaterFive());
	if (it == v.end())
	{
		cout << "未找到" << endl;
	}
	else
	{
		cout << "找到大于5的数字为" << *it << endl;
	}
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
## 44.3 二元谓词
```cpp
#include<vector>
#include<algorithm>
#include<iostream>
using namespace std;

class MyCompare
{
public:
	bool operator()(int val1, int val2)// 二元谓词
	{
		return val1 > val2;
	}
};

void test01()
{
	vector<int>v;
	v.push_back(10);
	v.push_back(40);
	v.push_back(20);
	v.push_back(30);
	v.push_back(50);

	// 默认从小到大
	sort(v.begin(), v.end());
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
	cout << "--------------------" << endl;

	// 使用函数对象改变算法策略，排序从大到小
	sort(v.begin(), v.end(), MyCompare());
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/fd6cd38e379a45fcaf450cdc90b0c149.png)
# 45 内建函数对象
## 45.1 内建函数对象意义
**概念：**
* STL内建了一些函数对象，#include\<functional>内建函数对象文件

**分类:**
* 算术仿函数
* 关系仿函数
* 逻辑仿函数

**用法：**
* 这些仿函数所产生的对象，用法和一般函数完全相同
* 使用内建函数对象，需要引入头文件 `#include<functional>`

## 45.2 算术仿函数
**功能描述：**
* 实现四则运算
* 其中negate是一元运算，其他都是二元运算

**仿函数原型：**
* `template<class T> T plus<T>`               加法仿函数
* `template<class T> T minus<T>`            减法仿函数
* `template<class T> T multiplies<T>`       乘法仿函数
* `template<class T> T divides<T>`          除法仿函数
* `template<class T> T modulus<T>`        取模仿函数
* `template<class T> T negate<T>`          取反仿函数

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
#include<functional>// 内建函数对象文件
using namespace std;

// 内建函数对象 算术仿函数

// negate 一元仿函数 取反仿函数
void test01()
{
	negate<int>n;
	cout << n(50) << endl;// -50
}

// plus 二元仿函数 加法
void test02()
{
	plus<int>p;// 默认是同种类型
	cout << p(10, 20) << endl;
}

int main()
{
	test01();
	test02();
	system("pause");
	return 0;
}
```
## 45.3 关系仿函数
**功能描述：**
- 实现关系对比

**仿函数原型：**
* `template<class T> bool equal_to<T>`                   等于
* `template<class T> bool not_equal_to<T>`             不等于
* `template<class T> bool greater<T>`                     大于
* `template<class T> bool greater_equal<T>`            大于等于
* `template<class T> bool less<T>`                          小于
* `template<class T> bool less_equal<T>`                 小于等于

**总结：**
 - 关系仿函数中最常用的就是greater<>大于

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
#include<functional>
using namespace std;

// 内建函数对象 关系仿函数
// 大于 greater函数和下面的仿函数MyCompare的作用一致
class MyCompare
{
public:
	bool operator()(int val1, int val2)
	{
		return val1 > val2;
	}
};

void test01()
{
	vector<int> v;

	v.push_back(10);
	v.push_back(30);
	v.push_back(50);
	v.push_back(40);
	v.push_back(20);

	// 降序 sort(v.begin(), v.end(), MyCompare());

	sort(v.begin(), v.end(), greater<int>());
	for (vector<int>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/f6be66d58eac49e68f3a4a6b965adbf4.png)

## 45.4 逻辑仿函数
**功能描述：**
- 实现逻辑运算

**函数原型：**
* `template<class T> bool logical_and<T>`              逻辑与
* `template<class T> bool logical_or<T>`                逻辑或
* `template<class T> bool logical_not<T>`              逻辑非

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
#include<functional>
using namespace std;

// 内建函数对象_逻辑仿函数
// 逻辑非 logical_not
void test01()
{
	vector<bool> v;
	v.push_back(true);
	v.push_back(false);
	v.push_back(true);
	v.push_back(false);

	for (vector<bool>::iterator it = v.begin(); it != v.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;

	// 逻辑非  将v容器搬运到v2中，并执行逻辑非运算
	vector<bool> v2;
	v2.resize(v.size());// 重新设置大小
	transform(v.begin(), v.end(), v2.begin(), logical_not<bool>());
	for (vector<bool>::iterator it = v2.begin(); it != v2.end(); it++)
	{
		cout << *it << " ";
	}
	cout << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/f81c8a40a6464957ba4aa34afcbbca92.png)	

# 提高5 STL常用算法

# 46 常用遍历算法
**学习目标：**
* 掌握常用的遍历算法

**算法简介：**
* `for_each`     遍历容器
* `transform`    搬运容器到另一个容器中

## 46.1 for_each
**功能描述：**
* 实现遍历容器

**函数原型：**
* `for_each(iterator beg, iterator end, _func);  ` 遍历算法 遍历容器元素；beg 开始迭代器；end 结束迭代器；_func 函数或者函数对象

**总结：**
 - for_each在实际开发中是最常用遍历算法，需要熟练掌握

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
using namespace std;

// 遍历算法 for_each

// 普通函数
void print01(int val)
{
	cout << val << " ";
}

// 仿函数，函数对象
class print02
{
public:
	void operator()(int val)
	{
		cout << val << " ";
	}
};

void test01()
{
	vector<int>v;
	for (int i = 0; i < 10; i++)
	{
		v.push_back(i);
	}
	for_each(v.begin(), v.end(), print01);// 最后是一个普通函数
	cout << endl;

	for_each(v.begin(), v.end(), print02());// print02需要传入匿名对象才可以遍历
	cout << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/8ce5b56659ea4f1885849511443eb6dc.png)	
## 46.2 transform
**功能描述：**
* 搬运容器到另一个容器中

**函数原型：**
* `transform(iterator beg1, iterator end1, iterator beg2, _func);` beg1 源容器开始迭代器；end1 源容器结束迭代器；beg2 目标容器开始迭代器；_func 函数或者函数对象

**总结：** 
- 搬运的目标容器必须要提前开辟空间，否则无法正常搬运
```cpp
#include<algorithm>//算法头文件
#include<iostream>
#include<vector>
using namespace std;

// transform搬运容器到另一个容器

// 仿函数
class Transform
{
public:
	int operator()(int v)
	{
		return v;// return v + 1000; 可以一边搬一边设计一些规则
	}
};

// 仿函数，打印函数
class MyPrint
{
public:
	void operator()(int val)
	{
		cout << val << " ";
	}
};

void test01()
{
	vector<int>v;// 原容器
	for (int i = 0; i < 10; i++)
	{
		v.push_back(i);
	}

	vector<int>vTarget;// 目标容器
	vTarget.resize(v.size());// 需要给目标容器提前开辟空间(重点), 防止崩溃
	// 使用仿函数可以实现一边向其他容器搬数据，一边按照逻辑规则做逻辑运算
	transform(v.begin(), v.end(), vTarget.begin(), Transform());

	for_each(vTarget.begin(), vTarget.end(), MyPrint());
	cout << endl;// 0 1 2 3 4 5 6 7 8 9
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
# 47 常用查找算法
**算法简介：**
- `find`                  查找元素
- `find_if`              按条件查找元素
- `adjacent_find`    查找相邻重复元素
- `binary_search`   二分查找法
- `count`               统计元素个数
- `count_if`            按条件统计元素个数
## 47.1 find
**功能描述：**
* 查找指定元素，找到返回指定元素的迭代器，找不到返回结束迭代器end()

**函数原型：**
- `find(iterator beg, iterator end, value);  `按值查找元素，找到返回指定位置迭代器，找不到返回结束迭代器位置，beg 开始迭代器，end 结束迭代器，value 查找的元素。

**总结：** 
- 利用find可以在容器中找指定的元素，返回值是**迭代器**
```cpp
#include<vector>
#include<algorithm>
#include<iostream>
#include<vector>
#include<string>
using namespace std;

// find——返回迭代器

// 1. 查找 内置数据类型
void  test01()
{
	vector<int>v;
	for (int i = 0; i < 10; i++)
	{
		v.push_back(i);
	}

	// 查找容器中是否有5这个元素
	vector<int>::iterator it = find(v.begin(), v.end(), 5);// find返回值为迭代器
	if (it == v.end())
	{
		cout << "没有找到元素5" << endl;
	}
	else
	{
		cout << "找到元素5" << endl;
	}
}

// 2. 查找 自定义数据类型
class Person
{
public:
	Person(string name, int age)
	{
		this->m_Name = name;
		this->m_Age = age;
	}
	string m_Name;
	int m_Age;

	// 重载 == 底层find 知道如何对比person数据类型
	bool operator==(const Person& p)// 引用方式传递，const防止修改
	{
		// 自身姓名/年龄和传进来的姓名/年龄一致
		if (this->m_Name == p.m_Name && this->m_Age == p.m_Age)
		{
			return true;
		}
		else
		{
			return false;
		}
	}
};

void test02()
{
	vector<Person> v;

	// 创建数据
	Person p1("aaa", 10);
	Person p2("bbb", 20);
	Person p3("ccc", 30);
	Person p4("ddd", 40);

	// 放到容器中
	v.push_back(p1);
	v.push_back(p2);
	v.push_back(p3);
	v.push_back(p4);

	Person pp("bbb", 20);

	vector<Person>::iterator it = find(v.begin(), v.end(), pp);
	if (it == v.end())
	{
		cout << "没有找到!" << endl;
	}
	else
	{
		cout << "找到姓名:" << it->m_Name << " 年龄: " << it->m_Age << endl;
	}
}

int main()
{
	test01();// 查找 内置数据类型
	cout << endl;
	test02();// 查找 自定义数据类型
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/95a10bf57d0c475f8954162544552f4a.png)
## 47.2 find_if(需要仿函数)
**功能描述：**
* 按条件查找元素

**函数原型：**
- `find_if(iterator beg, iterator end, _Pred);  `
- 按值查找元素，找到返回指定位置迭代器，找不到返回结束迭代器位置。
- beg 开始迭代器；
- end 结束迭代器；
- _Pred 函数或者谓词（返回bool类型的仿函数）就是说需要写一个仿函数

**总结：**
- find_if 按条件查找使查找更加灵活，提供的仿函数可以改变不同的策略
```cpp
#include<algorithm>
#include<vector>
#include<string>
#include<iostream>
using namespace std;

// 常用查找算法 find_if
// find_if(iterator beg, iterator end, _Pred) 最后返回的是谓词

// 1、查找内置数据类型，带条件的查找，比如大于5
class GreaterFive
{
public:
	bool operator()(int val)
	{
		return val > 5;
	}
};

void test01()
{
	vector<int> v;
	for (int i = 0; i < 10; i++)
	{
		v.push_back(i + 1);
	}

	vector<int>::iterator it = find_if(v.begin(), v.end(), GreaterFive());// 返回迭代器

	if (it == v.end()) {
		cout << "没有找到!" << endl;
	}
	else {
		cout << "找到大于5的数字: " << *it << endl;
	}
}

// 2、查找自定义数据类型
class Person {
public:
	Person(string name, int age)
	{
		this->m_Name = name;
		this->m_Age = age;
	}
public:
	string m_Name;
	int m_Age;
};

class Greater20
{
public:
	bool operator()(Person& p)
	{
		return p.m_Age > 20;
	}
};

void test02() {

	vector<Person> v;

	// 创建数据
	Person p1("aaa", 10);
	Person p2("bbb", 20);
	Person p3("ccc", 30);
	Person p4("ddd", 40);

	v.push_back(p1);
	v.push_back(p2);
	v.push_back(p3);
	v.push_back(p4);

	vector<Person>::iterator it = find_if(v.begin(), v.end(), Greater20());
	if (it == v.end())
	{
		cout << "没有找到!" << endl;
	}
	else
	{
		cout << "找到姓名: " << it->m_Name << " 年龄: " << it->m_Age << endl;
	}
}

int main() {

	test01();
	cout << endl;
	test02();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/b178463300674deaa9cf16ba81b0ccae.png)	
## 47.3 adjacent_find
**功能描述：**
* 查找相邻重复元素

**函数原型：**
- `adjacent_find(iterator beg, iterator end);  `
- 查找相邻重复元素，返回相邻元素的第一个位置的迭代器；
- beg 开始迭代器；end 结束迭代器

**总结：**
- 面试题中如果出现查找相邻重复元素，记得用STL中的adjacent_find算法
```cpp
#include<vector>
#include<algorithm>
#include<iostream>
using namespace std;

// 常用查找算法 adjacent_find，查找相邻重复元素
// 有的话返回相邻元素第1个元素的迭代器，没有的话返回end迭代器位置
void test01()
{
	vector<int> v;
	v.push_back(0);
	v.push_back(2);
	v.push_back(0);
	v.push_back(3);
	v.push_back(1);
	v.push_back(4);
	v.push_back(3);
	v.push_back(3);

	vector<int>::iterator pos = adjacent_find(v.begin(), v.end());// 返回迭代器
	if (pos == v.end())
	{
		cout << "未找到相邻重复元素" << endl;
	}
	else
	{
		cout << "找到相邻重复元素：" << *pos << endl;
	}
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/8425f0cc9b5e410c8a07f4538a2f3aec.png)
## 47.4 binary_search
**功能描述：**
* 查找指定元素是否存在，返回的是false或者true

**函数原型：**
- `bool binary_search(iterator beg, iterator end, value);  `
- 查找指定的元素，查到 返回true  否则false
- 注意: 在**无序序列中不可用**
- beg 开始迭代器
- end 结束迭代器
- value 查找的元素

**总结：**
- 二分查找法查找效率很高，值得注意的是查找的容器中元素必须的**有序序列**
```cpp
#include<vector>
#include<algorithm>
#include<iostream>
using namespace std;

// 返回的不是迭代器，返回的是bool类型
void test01()
{
	vector<int>v;

	for (int i = 0; i < 10; i++)
	{
		v.push_back(i);
	}
	// 二分查找：查找容器中是否有元素2
	// 注意，容器必须是有序的序列，如果是无序序列，结果未知
	bool ret = binary_search(v.begin(), v.end(), 2);
	if (ret)
	{
		cout << "找到了" << endl;
	}
	else
	{
		cout << "未找到" << endl;
	}
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
## 47.5 count
**功能描述：**
* 统计元素个数

**函数原型：**
- `count(iterator beg, iterator end, value);  `统计元素出现次数
- beg 开始迭代器
- end 结束迭代器
- value 统计的元素

**总结：**
- 统计自定义数据类型时候，需要配合重载 `operator==`

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
using namespace std;

// 1. 统计内置数据类型
void test01()
{
	vector<int> v;
	v.push_back(1);
	v.push_back(2);
	v.push_back(4);
	v.push_back(5);
	v.push_back(3);
	v.push_back(4);
	v.push_back(4);

	int num = count(v.begin(), v.end(), 4);

	cout << "4 的个数为： " << num << endl;
}

// 2. 统计自定义数据类型
class Person
{
public:
	Person(string name, int age)
	{
		this->m_Name = name;
		this->m_Age = age;
	}
	bool operator==(const Person& p)// 告诉代码根据什么进行统计，这里是按照年龄
	{
		if (this->m_Age == p.m_Age)
		{
			return true;
		}
		else
		{
			return false;
		}
	}
	string m_Name;
	int m_Age;
};

void test02()
{
	vector<Person> v;

	Person p1("刘备", 35);
	Person p2("关羽", 35);
	Person p3("张飞", 35);
	Person p4("赵云", 30);
	Person p5("曹操", 25);

	v.push_back(p1);
	v.push_back(p2);
	v.push_back(p3);
	v.push_back(p4);
	v.push_back(p5);

	Person p("诸葛亮", 35);

	int num = count(v.begin(), v.end(), p);// 统计年龄35岁
	cout << "和诸葛亮同岁的人的个数： " << num << endl;
}

int main()
{
	test01();
	test02();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/32229e77392347ad88e0a6a8f3b07fe6.png)	
## 47.6 count_if(需要仿函数)
**功能描述：**
* 按条件统计元素个数

**函数原型：**
- `count_if(iterator beg, iterator end, _Pred);  `    按条件统计元素出现次数
- beg 开始迭代器；
- end 结束迭代器；
- _Pred 谓词，需要写一个仿函数

**总结：**
- 按值统计用count，按条件统计用count_if
```cpp
#include<vector>
#include<algorithm>
#include<iostream>
using namespace std;

// 常见查找算法 count_if，_Pred表示需要提供谓词

class Greater4
{
public:
	bool operator()(int val)
	{
		return val >= 4;
	}
};

// 1. 统计内置数据类型
void test01()
{
	vector<int> v;
	v.push_back(1);
	v.push_back(2);
	v.push_back(4);
	v.push_back(5);
	v.push_back(3);
	v.push_back(4);
	v.push_back(4);

	int num = count_if(v.begin(), v.end(), Greater4());// 最后是谓词，需要写一个仿函数

	cout << "大于4的个数为：" << num << endl;
}

// 2. 统计自定义数据类型
class Person
{
public:
	Person(string name, int age)
	{
		this->m_Name = name;
		this->m_Age = age;
	}
	string m_Name;
	int m_Age;
};

class AgeLess35 // 仿函数
{
public:
	bool operator()(const Person& p)
	{
		return p.m_Age < 35;
	}
};

void test02()
{
	vector<Person> v;

	Person p1("刘备", 35);
	Person p2("关羽", 35);
	Person p3("张飞", 35);
	Person p4("赵云", 30);
	Person p5("曹操", 25);

	v.push_back(p1);
	v.push_back(p2);
	v.push_back(p3);
	v.push_back(p4);
	v.push_back(p5);

	int num = count_if(v.begin(), v.end(), AgeLess35());// 最后是谓词，需要写一个仿函数
	cout << "小于35岁的个数：" << num << endl;
}

int main() {

	test01();
	test02();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/5434fe9a7f0742449b7c9beebdfa0df5.png)	
# 48 常用排序算法
**学习目标：**
- 掌握常用的排序算法

**算法简介：**
- `sort`             对容器内元素进行排序
- `random_shuffle`  洗牌   指定范围内的元素随机调整次序
- `merge `           容器元素合并，并存储到另一容器中
- `reverse`         反转指定范围的元素
## 48.1 sort 
**功能描述：**
* 对容器内元素进行排序

**函数原型：**
- `sort(iterator beg, iterator end, _Pred);  ` 按值查找元素，找到返回指定位置迭代器，找不到返回结束迭代器位置
- beg   开始迭代器
- end    结束迭代器
- _Pred  谓词，默认是从小到大排序，如果是其他排序方式，需要写一个仿函数

**总结：**
- sort属于开发中最常用的算法之一，需熟练掌握
```cpp
#include<vector>
#include<algorithm>
#include<iostream>
#include<functional>
using namespace std;

// 排序算法sort
void myPrint(int val)
{
	cout << val << " ";
}

void test01()
{
	vector<int>v;
	v.push_back(10);
	v.push_back(30);
	v.push_back(50);
	v.push_back(20);
	v.push_back(40);

	// 利用sort进行排序，默认从小到大
	sort(v.begin(), v.end());
	for_each(v.begin(), v.end(), myPrint);// 10 20 30 40 50
	cout << endl;

	// 改为降序
	sort(v.begin(), v.end(), greater<int>());// greater表示从大到小排序
	for_each(v.begin(), v.end(), myPrint);// 50 40 30 20 10
	cout << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
## 48.2 random_shuffle
**功能描述：**
* 洗牌   指定范围内的元素随机调整次序

**函数原型：**
 - `random_shuffle(iterator beg, iterator end);  ` 指定范围内的元素随机调整次序
 - beg 开始迭代器
 - end 结束迭代器

 **总结：**
 - random_shuffle洗牌算法比较实用，使用时记得加随机数种子

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
#include<ctime>// 随机种子
using namespace std;

// 打印函数
void myPrint(int val)
{
	cout << val << " ";
}

void test01()
{
	srand((unsigned int)time(NULL));// 随机数种子，可以生成任意排列的0-9的顺序

	vector<int>v;
	for (int i = 0; i < 10; i++)
	{
		v.push_back(i);
	}
	for_each(v.begin(), v.end(), myPrint);
	cout << endl;

	// 利用洗牌算法打乱顺序
	random_shuffle(v.begin(), v.end());

	cout << "洗牌后" << endl;
	for_each(v.begin(), v.end(), myPrint);
	cout << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/201a476cf00340ebb7151f3a17ef6aa9.png)	
## 48.3 merge
**功能描述：**
* 两个容器元素合并，并存储到另一容器中

**函数原型：**
- `merge(iterator beg1, iterator end1, iterator beg2, iterator end2, iterator dest);  ` 容器元素合并，并存储到另一容器中
- 注意: 两个容器必须是**有序的**
- beg1   容器1开始迭代器
- end1   容器1结束迭代器
- beg2   容器2开始迭代器
- end2   容器2结束迭代器
- dest    目标容器开始迭代器

**总结：**
 - merge合并的两个容器必须的有序序列

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
using namespace std;

// 排序算法 merge
void myPrint(int val)
{
	cout << val << " ";
}

void test01()
{
	vector<int>v1;
	vector<int>v2;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
		v2.push_back(i + 1);
	}

	// 目标容器
	vector<int>vTarget;

	// 目标容器需要提前开辟空间!!!!!
	vTarget.resize(v1.size() + v2.size());

	// 合并  需要两个有序序列,合并后还是有序序列
	merge(v1.begin(), v1.end(), v2.begin(), v2.end(), vTarget.begin());

	for_each(vTarget.begin(), vTarget.end(), myPrint);
	cout << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
## 48.4 reverse
**功能描述：**
* 将容器内元素进行反转

**函数原型：**
- `reverse(iterator beg, iterator end);  `反转指定范围的元素
- beg 开始迭代器
- end 结束迭代器

**总结：**
- reverse反转区间内元素，面试题可能涉及到
```cpp
#include<vector>
#include<algorithm>
#include<iostream>
using namespace std;

// 常用排序算法reverse
void myPrint(int val)
{
	cout << val << " ";
}

void test01()
{
	vector<int>v;
	v.push_back(10);
	v.push_back(30);
	v.push_back(50);
	v.push_back(20);
	v.push_back(40);

	cout << "反转前： " << endl;

	for_each(v.begin(), v.end(), myPrint);
	cout << endl;

	cout << "反转后： " << endl;

	reverse(v.begin(), v.end());
	for_each(v.begin(), v.end(), myPrint);// myPrint不需要加()
	cout << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/b5950594b0054ceebe0894847039b854.png)	

# 49 常用拷贝和替换算法
**学习目标：**
- 掌握常用的拷贝和替换算法

**算法简介：**
- `copy`                  容器内指定范围的元素拷贝到另一容器中
- `replace`              将容器内指定范围的旧元素修改为新元素
- `replace_if `          容器内指定范围满足条件的元素替换为新元素
- `swap`                 互换两个容器的元素
## 49.1 copy 拷贝 
**功能描述：**
* 容器内指定范围的元素拷贝到另一容器中

**函数原型：**
- `copy(iterator beg, iterator end, iterator dest);  `按值查找元素，找到返回指定位置迭代器，找不到返回结束迭代器位置
- beg  开始迭代器
- end  结束迭代器
- dest 目标起始迭代器

**总结：**
- 利用copy算法在拷贝时，目标容器记得提前开辟空间

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
using namespace std;

// copy算法
class myPrint
{
public:
	void operator()(int val)
	{
		cout << val << " ";
	}
};

void test01()
{
	vector<int> v1;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i + 1);
	}
	vector<int> v2;
	v2.resize(v1.size());// 设置v2的大小，提前开辟空间
	copy(v1.begin(), v1.end(), v2.begin());

	for_each(v2.begin(), v2.end(), myPrint());
	cout << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
## 49.2 replace 替换 
**功能描述：**
* 将容器内指定范围的旧元素修改为新元素

**函数原型：**
- `replace(iterator beg, iterator end, oldvalue, newvalue);  `将区间内**旧元素替换成新元素**
- beg 开始迭代器
- end 结束迭代器
- oldvalue 旧元素
- newvalue 新元素

**总结：**
- replace会替换区间内满足条件的元素

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
using namespace std;

// 替换replace
class myPrint
{
public:
	void operator()(int val)
	{
		cout << val << " ";
	}
};

void test01()
{
	vector<int> v;
	v.push_back(20);
	v.push_back(30);
	v.push_back(20);
	v.push_back(40);
	v.push_back(50);
	v.push_back(10);
	v.push_back(20);

	cout << "替换前：" << endl;
	for_each(v.begin(), v.end(), myPrint());
	cout << endl;

	// 将容器中的20 替换成 2000
	cout << "替换后：" << endl;
	replace(v.begin(), v.end(), 20, 2000);
	for_each(v.begin(), v.end(), myPrint());
	cout << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/e01c0bf1e11d408b9c315f066b593535.png)	
## 49.3  replace_if 替换
**功能描述:**  
* 将区间内满足条件的元素，替换成指定元素

**函数原型：**
- `replace_if(iterator beg, iterator end, _pred, newvalue);  `按条件替换元素，满足条件的替换成指定元素
- beg 开始迭代器
- end 结束迭代器
- _pred 谓词
- newvalue 替换的新元素

**总结：**
- replace_if按条件查找，可以利用仿函数灵活筛选满足的条件

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
using namespace std;

// 替换replace_if
class myPrint
{
public:
	void operator()(int val)
	{
		cout << val << " ";
	}
};

// 替换大于等于30的为300，谓词
class Greater30
{
public:
	bool operator()(int val)
	{
		return val >= 30;// 该条件下进行替换
	}
};

void test01()
{
	vector<int> v;
	v.push_back(20);
	v.push_back(30);
	v.push_back(20);
	v.push_back(40);
	v.push_back(50);
	v.push_back(10);
	v.push_back(20);

	cout << "替换前：" << endl;
	for_each(v.begin(), v.end(), myPrint());
	cout << endl;

	// 大于等于30的替换成300
	replace_if(v.begin(), v.end(), Greater30(), 300);
	cout << "替换后：" << endl;
	for_each(v.begin(), v.end(), myPrint());
	cout << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/161129a8600e467c87d65033aca51bf2.png)	
## 49.4 swap 互换 
**功能描述：**
* 互换两个容器的元素

**函数原型：**
- `swap(container c1, container c2);  `互换两个容器的元素
- c1容器1
- c2容器2

**总结：**
- swap交换容器时，注意交换的容器要同种类型

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
using namespace std;

// 互换swap
class myPrint
{
public:
	void operator()(int val)
	{
		cout << val << " ";
	}
};

void test01()
{
	vector<int> v1;
	vector<int> v2;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
		v2.push_back(i + 100);
	}

	cout << "交换前： " << endl;
	for_each(v1.begin(), v1.end(), myPrint());
	cout << endl;
	for_each(v2.begin(), v2.end(), myPrint());
	cout << endl;

	cout << "交换后： " << endl;
	swap(v1, v2);
	for_each(v1.begin(), v1.end(), myPrint());
	cout << endl;
	for_each(v2.begin(), v2.end(), myPrint());
	cout << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/851eea3776ae4c6486142111b4145fb5.png)
# 50 算术生成算法(\<numeric>)
**学习目标：**
- 掌握常用的算术生成算法

**注意：**
* 算术生成算法属于小型算法，使用时包含的头文件为 `#include <numeric>`

**算法简介：**
- `accumulate`     计算容器元素累计总和
- `fill`                 向容器中添加元素

## 50.1 accumulate 累计总和 
**功能描述：**
*  计算区间内 容器元素累计总和

**函数原型：**
- `accumulate(iterator beg, iterator end, value);  `计算容器元素累计总和
- beg 开始迭代器
- end 结束迭代器
- value 起始值

**总结：**
- accumulate使用时头文件注意是 numeric，这个算法很实用

```cpp
#include<vector>
#include<numeric>
#include<algorithm>
#include<iostream>
using namespace std;

void test01()
{
	vector<int> v;
	for (int i = 0; i <= 100; i++) {
		v.push_back(i);
	}

	int total = accumulate(v.begin(), v.end(), 0);// 0为起始累加值

	cout << "total = " << total << endl;// 5050
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
## 50.2 fill 指定元素 
**功能描述：**
* 向容器中填充指定的元素

**函数原型：**
- `fill(iterator beg, iterator end, value);  ` 向容器中填充元素
- beg 开始迭代器
- end 结束迭代器
- value 填充的值

**总结：**
- 利用fill可以将容器区间内元素填充为 指定的值

```cpp
#include<vector>
#include<algorithm>
#include<iostream>
using namespace std;

class myPrint
{
public:
	void operator()(int val)
	{
		cout << val << " ";
	}
};

void test01()
{
	vector<int> v;
	v.resize(10);

	// 后期重新填充
	fill(v.begin(), v.end(), 100);

	for_each(v.begin(), v.end(), myPrint());
	cout << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/7357928fda8c4dbe9b428b8102b5e62b.png)
# 51 常用集合算法
**学习目标：**
- 掌握常用的集合算法

**算法简介：**
- `set_intersection`         求两个容器的交集
- `set_union`                 求两个容器的并集
- `set_difference `          求两个容器的差集

![在这里插入图片描述](https://img-blog.csdnimg.cn/35179c52695f43818cd27a3d05731d8f.png)
## 51.1 set_intersection 交集 
**功能描述：**
* 求两个容器的交集

**函数原型：**
- `set_intersection(iterator beg1, iterator end1, iterator beg2, iterator end2, iterator dest);  `求两个集合的交集
- **注意:两个集合必须是有序序列**
- beg1 容器1开始迭代器
- end1 容器1结束迭代器
- beg2 容器2开始迭代器
- end2 容器2结束迭代器
- dest 目标容器开始迭代器

**总结：** 
* 求交集的两个集合必须的有序序列
* 目标容器开辟空间需要从**两个容器中取小值**
* set_intersection返回值既是交集中最后一个元素的位置

```cpp
#include<iostream>
#include<vector>
#include<algorithm>
using namespace std;

class myPrint
{
public:
	void operator()(int val)
	{
		cout << val << " ";
	}
};

void test01()
{
	vector<int> v1;
	vector<int> v2;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
		v2.push_back(i + 5);
	}

	vector<int> vTarget;
	// 目标容器需要提前开辟空间
	// 最特殊的情况 大容器包含小容器 开辟空间 取小容器的size即可
	vTarget.resize(min(v1.size(), v2.size()));

	// 返回目标容器的最后一个元素的迭代器地址
	vector<int>::iterator itEnd = set_intersection(v1.begin(), v1.end(), v2.begin(), v2.end(), vTarget.begin());

	for_each(vTarget.begin(), itEnd, myPrint());// 返回值是最后迭代器的位置
	cout << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
## 51.2 set_union 并集 
**功能描述：**
* 求两个集合的并集

**函数原型：**
- `set_union(iterator beg1, iterator end1, iterator beg2, iterator end2, iterator dest);  ` 求两个集合的并集
- **注意:两个集合必须是有序序列**
- beg1 容器1开始迭代器
- end1 容器1结束迭代器
- beg2 容器2开始迭代器
- end2 容器2结束迭代器
- dest 目标容器开始迭代器

**总结：** 
- 求并集的两个集合必须的有序序列
- 目标容器开辟空间需要**两个容器相加**
- set_union返回值既是并集中最后一个元素的位置

```cpp
#include<iostream>
#include<vector>
#include<algorithm>
using namespace std;

class myPrint // 打印函数
{
public:
	void operator()(int val)
	{
		cout << val << " ";
	}
};

void test01()
{
	vector<int> v1;
	vector<int> v2;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
		v2.push_back(i + 5);
	}

	vector<int> vTarget;
	// 取两个容器的和给目标容器开辟空间
	vTarget.resize(v1.size() + v2.size());

	// 返回目标容器的最后一个元素的迭代器地址
	vector<int>::iterator itEnd = set_union(v1.begin(), v1.end(), v2.begin(), v2.end(), vTarget.begin());

	for_each(vTarget.begin(), itEnd, myPrint());// 使用最后的迭代器itend
	cout << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
## 51.3 set_difference 差集 
**功能描述：**
* 求两个集合的差集

**函数原型：**
- `set_difference(iterator beg1, iterator end1, iterator beg2, iterator end2, iterator dest);  `求两个集合的差集
- **注意:两个集合必须是有序序列**
- beg1 容器1开始迭代器
- end1 容器1结束迭代器
- beg2 容器2开始迭代器
- end2 容器2结束迭代器
- dest 目标容器开始迭代器

**总结：** 
- 求差集的两个集合必须的有序序列
- 目标容器开辟空间需要从**两个容器取较大值**
- set_difference返回值既是差集中最后一个元素的位置
```cpp
#include<vector>
#include<algorithm>
#include<iostream>
using namespace std;

// 差集set_difference
class myPrint
{
public:
	void operator()(int val)
	{
		cout << val << " ";
	}
};

void test01()
{
	vector<int> v1;
	vector<int> v2;
	for (int i = 0; i < 10; i++)
	{
		v1.push_back(i);
		v2.push_back(i + 5);
	}

	vector<int> vTarget;
	// 取两个里面较大的值给目标容器开辟空间
	vTarget.resize(max(v1.size(), v2.size()));

	// 返回目标容器的最后一个元素的迭代器地址
	cout << "v1 与 v2 的差集为： " << endl;
	vector<int>::iterator itEnd = set_difference(v1.begin(), v1.end(), v2.begin(), v2.end(), vTarget.begin());
	for_each(vTarget.begin(), itEnd, myPrint());
	cout << endl;

	cout << endl;

	cout << "v2 与 v1 的差集为： " << endl;
	itEnd = set_difference(v2.begin(), v2.end(), v1.begin(), v1.end(), vTarget.begin());
	for_each(vTarget.begin(), itEnd, myPrint());
	cout << endl;
}

int main()
{
	test01();
	system("pause");
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/003b04e1890d4b0db8f7d36948cc5492.png)	