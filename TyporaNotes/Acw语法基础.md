学习编程语言语法是次要的，思维是主要的。如何把头脑中的想法变成简洁的代码，至关重要

# 1 变量、输入输出、顺序语句

## 1. 变量的定义
- 变量必须先定义，才可以使用，不能重名
- 变量定义的方式如下

```cpp
#include<iostream>
using namespace std;

int main()
{
	int a = 5;
	int b = a, d = 10/2;
	return 0;
}
```
|   类型   | 关键字 |
| :------: | :----: |
|  布尔型  |  bool  |
|  字符型  |  char  |
|   整型   |  int   |
| 浮点数型 | float  |
| 双浮点型 | double |
## 2. 输入输出
### 2.1 整数的输入输出
```cpp
#include<iostream>
using namespace std;

int main()
{
	int a,b;
	cin >> a >> b;
	count << a+b << endl;
	return 0;
}
```
### 2.2 字符串的输入输出

```cpp
#include<iostream>
#include<string>

using namespace std;

int main()
{
	string str;
	cin >> str;
	cout << str;
	return 0;
}
```
### 2.3 输入输出多个不同类型的变量

```cpp
#include<iostream>
#include<string>
using namespace std;

int main()
{
	int a, b;
	string str;
	
	cin >> a;
	cin >> b >> str;

	cout << str << "!!!" << a+b << endl;
	return 0;
}
```
## 3. 表达式
### 3.1 整数的加减乘除四则运算

```cpp
#include<iostream>
#include<string>
using namespace std;

int main()
{
	int a = 6 + 3 * 4 / 2 - 2;
	cout << a << endl;
	int b = a * 10 + 5 / 2;
	cout << b << endl;
	cout << 23 * 56 - 78 / 3 << endl;
	
	return 0;
}
```
| 运算符 | 描述                     | 实例            |
| ------ | ------------------------ | --------------- |
| +      | 把两个操作数相加         | A + B 得到 30   |
| -      | 操作数1减去操作数2       | A  - B 得到 -10 |
| *      | 两个操作数相乘           | A * B 得到 200  |
| /      | 分子除以分母             | B / A 得到 2    |
| %      | 取模运算符，整数后的余数 | B % A 得到 0    |

### 3.2 浮点数(小数)运算

```cpp
#include<iostream>
#include<string>
using namespace std;

int main()
{
	float x = 1.5, y = 3.2;
	cout << x * y << ' ' << x + y << endl;
	cout << x - y << ' ' << x / y << endl;
	return 0;
}
```
### 3.3 整数变量的自增自减

```cpp
#include<iostream>
#include<string>
using namespace std;

int main()
{
	int a = 1;
	int b = a ++;
	cout << a << ' '<< b << endl;
	int c = ++ a;
	cout << a << ' '<< c << endl;
	return 0;
}
```
### 3.4 变量的类型转换

```cpp
#include<iostream>
#include<string>
using namespace std;

int main()
{
	float x = 123.12;
	int y = (int)x;
	cout << x << ' ' << y << endl;
	return 0;
}
```
## 4. 顺序语句
### 4.1 输出第二个整数

```cpp
#include<iostream>
#include<string>
using namespace std;

int main()
{
	int a, b, c;
	cin >> a >> b >> c;
	cout << b << endl;
	return 0;
}
```
### 4.2 计算 (a + b) * c 的值

```cpp
#include<iostream>
#include<string>
using namespace std;

int main()
{
	int a, b, c;
	cin >> a >> b >> c;
	cout << (a + b) * c << endl;
	return 0;
}
```
### 4.3 带余除法

```cpp
#include<iostream>
#include<string>
using namespace std;

int main()
{
	int a, b;
	cin >> a >> b;
	int c = a / b, d = a % b;
	cout << c << ' ' << d << endl;
	return 0;
}
```
### 4.4 求反三位数

```cpp
#include<iostream>
#include<string>
using namespace std;

int main()
{
	int n;
	cin >> n;
	
	int a = n % 10;// 个位
	n = n / 10;
	int b = n % 10;// 十位
	n = n / 10;
	int c = n;// 百位

	cout << a << b << c << endl;
	return 0;
}
```
### 4.5 输出菱形

```cpp
#include<iostream>
#include<string>
using namespace std;

int main()
{
	char c;
	cin >> c;
	cout << "  " << c << endl;
	cout << " " << c << c << c << endl;
	cout << c << c << c << c << c << endl;
	cout << "  " << c << endl;
	return 0;
}
```
## 5. 其他
### 5.1 浮点数的比较

```cpp
#include<iostream>
#include<cmath>
using namespace std;

const double eps=1e-6

int main()
{
    double x = 1.23456789;
    double a = x*x;
    double b =sqrt(a);
    
    printf("%.10f\n",b);
    if(fabs(x-b)<eps) puts("相等");
    
    return 0;
}
```
### 5.2  A + B(scanf中间会入读空格)

```cpp
#include<cstdio>
#include<iostream>

using namespace std;

int main()
{
    int a,b;
    scanf("%d%d",&a,&b);
    printf("a+b=%d\na*b=%d\n",a+b,a*b);
    
    char a,b;//会读入空格，所以输入中间不能有空格
    scanf("%c%c",&a,&b);
    printf("%c %c\n",a,b);
    
    // int:%d
    // float:%f
    // double:%lf
    // char:%c
    return 0;
}
```
### 5.3 hello world

```cpp
#include<cstido>
#include<iostream>

using namespace std;

int main()
{
    cout << "Hello World" << endl;
    
    bool false/true;    1byte 1字节   1Byte=8bit 1字节=8比特
    char 'a','b',' ','\n';  1byte
    int -2147483648~2147483647  4byte
    float 1.23,1.23e-2,6-7有效数字  4byte
    double 15-16有效数字    8byte
    
    long long -2^63~2^63-1  8byte
    long double 18到19位
    
    return 0;
}
```

# 2 printf 语句与判断结构

 - 学习语言最好的方式就是实践，每当掌握一个新功能时，就要立即将这个功能应用到实践中

## 1. printf 输出格式\<cstdio>
注意：使用 printf 时最好添加头文件 **#include \<cstdio>**

```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
	printf("HELLO WORLD!");
	return 0;
}
```
### 1.1 int、float、double、char 等输出格式
| 类型   | 格式 | 说明                         |
| ------ | ---- | ---------------------------- |
| int    | %d   | 整型                         |
| float  | %f   | 默认保留 6 位小数            |
| double | %lf  | 默认保留 6 位小数            |
| char   | %c   | 回车也是一个字符，用’\n’表示 |

```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
	int a = 3;
	float b = 3.12345678;
	double c = 3.12345678;
	char d = 'y';

	printf("%d\n", a);
	printf("%f\n", b);
	printf("%lf\n", c);
	printf("%c\n", d);
	return 0;
}
```
### 1.2 所有输出的变量均可在一个字符串
```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
	int a = 3;
	float b = 3.12345678;
	double c = 3.12345678;
	char d = 'y';
	
	printf("int a = %d,float b = %f\n,double c = %lf, char d = %c\n",a, b, c, d);
	return 0;
}
```
#### 1.2.1 练习1 菱形
 - 输入一个字符，用这个字符输出一个菱形

```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
	char c;
	cin >> c;
	printf("  %c\n",c);
	printf(" %c%c%c\n",c,c,c);
	printf("%c%c%c%c%c\n",c,c,c,c,c);
	printf(" %c%c%c\n",c,c,c);
	printf("  %c\n",c);
	return 0;
}
```
#### 1.2.2 练习2 时间
 - 输入一个整数，表示时间，单位是秒；输出一个字符串，用”时:分:秒”的形式表示这个时间

```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
	int t;
	cin >> t;
	int hours = t / 3600;
	int minutes = t % 3600 / 60;
	int seconds = t % 60;

	printf("%d:%d:%d\n",hours, minutes, seconds);
	return 0;
}
```
### 1.3 保留小数
 - float, double 等输出保留若干位小数时用：%.4f, %3lf

```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
	float b = 3.12345678;
	double c = 3.12345678;,float类型
,double类型
	printf("%.4f\n",b);// 3.1235,float类型
	printf("%.3lf\n",c);// 3.123,double类型
	return 0;
}
```
 - 最小数字宽度
 - %8.3f, 表示这个浮点数的最小宽度为 8，保留 3 位小数，当**宽度不足时在前面补空格**

```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
	int a = 3;
	float b = 3.12345678;
	double c = 3.12345678;

	printf("%5d\n",a);
	printf("%8.4f\n",b);
	printf("%7.3lf\n",c);
	return 0;
}
```
 - %-8.3f，表示最小宽度为 8，保留 3 位小数，当**宽度不足时在后面补上空格**

```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
	int a = 3;
	float b = 3.12345678;
	double c = 3.12345678;

	printf("%-5d\n",a);
	printf("%-8.4f\n",b);
	printf("%-7.3lf\n",c);
	return 0;
    /*
    3    
    3.1235  
    3.123  
    */
}
```

 - %08.3f, 表示最小宽度为 8，保留 3 位小数，当**宽度不足时在前面补上0**

```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
	int a = 3;
	float b = 3.12345678;
	double c = 3.12345678;

	printf("%05d\n",a);
	printf("%08.4f\n",b);
	printf("%07.3lf\n",c);
	return 0;
    /*
    00003
    003.1235
    003.123
	*/
}
```

## 2. if 语句
### 2.1 基本 if-else 语句
 - 当条件成立时，执行某些语句；否则执行另一些语句

```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
	int a = 3;
	cin >> a;

	if(a > 5)
	{
		printf("%d is big!\n",a);
		printf("%d + 1 = %d\n",a ,a+1);
	}
	else
	{
		printf("%d is small!\n",a);
		printf("%d - 1 = %d\n",a ,a-1);
	}
	return 0;
}
```
 - else 语句可以省略

```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
	int a = 3;
	cin >> a;

	if(a > 5)
	{
		printf("%d is big!\n",a);
		printf("%d + 1 = %d\n",a ,a+1);
	}
	return 0;
}
```
 - **当只有一条语句时，大括号可以省略**
```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
	int a = 3;
	cin >> a;

	if(a > 5)
		printf("%d is big!\n",a);
	else
		printf("%d is small!\n",a);
	return 0;
}
```
#### 2.1.1 练习1 
 - 输入一个整数，输出这个数的绝对值

```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
	int x;
	cin >> x;
	if(x > 0) cout << x << endl;
	else cout << -x << endl;
	return 0;
}
```
#### 2.1.2 练习2
 - 输入两个整数，输出两个数中较大的那个

```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
	int a, b;
	cin >> a >> b;

	if(a > b)
		cout << a << endl;
	else
		cout << b <<endl;
	return 0;
}
```
#### 2.1.3 练习3
 - If-else 语句内部也可以是 if-else 语句
 - 输入三个整数，输出三个数中最大的那个
```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
	int a, b, c;
	cin >> a >> b >> c;

	if(a > b)
	{
    	if (a > c) cout << a << endl;
    	else cout << c << endl;
    }
	else
	{
		if (b > c) cout << b << endl;
    	else cout << c << endl;
	}
	return 0;
}
```
### 2.2 常用比较运算符
|   含义   | 符号 |
| :------: | :--: |
|   大于   |  >   |
|   小于   |  <   |
| 大于等于 |  >=  |
| 小于等于 |  <=  |
|   等于   |  ==  |
|  不等于  |  !=  |

### 2.3 if else 连写
 - 输入一个 0 到 100 之间的分数，如果大于等于 85，输出 A；如果大于等于 70 并且小于 85，输出 B；如果大于等于 60 并且小于 70，输出 C；如果小于 60，输出 D；

```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
	int s;
	cin >> s;
	
	if(s >= 85)
	{
		printf("A");
	}
	else if (s >= 70)
	{
		printf("B");
	}
	else if(s >= 60)
	{
		printf("C");
	}
	else
	{
		printf("D");
	}
	return 0;
}
```

#### 2.3.1 练习1(重点)
 - 简单计算器输入两个数，以及一个运算符+, -, *, /，输出这两个数运算后的结果。当运算符是/，且除数是 0 时，输出”Divided by zero!”; 当输入的字符不是+, -, *, /时，输出”Invalid operator!”
 - ![在这里插入图片描述](https://img-blog.csdnimg.cn/cf2392abee9946ccb44388fc7821816f.png)

#### 2.3.1 练习2

 - 判断闰年。闰年有两种情况：(1) 能被 100 整除时，必须能被 400 整除；(2) 不能被 100 整除时，被 4 整除即可
 - 输入一个年份，如果是闰年输出 yes，否则输出 no

```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int mian()
{
	int year;
	cin >> year;
	
	if(year % 100 == 0)
	{
		if(year % 400 == 0) cout << "yes" << endl;
		else cout << "no" endl;
	}
	else
	{
		if(year % 4 == 0) cout << "yes" << endl;
		else cout << "no" endl;
	}
}
return 0;
```

## 3. 条件表达式
| 含义 | 符号 |
| :--: | :--: |
|  与  |  &&  |
|  或  | \|\| |
|  非  |  ！  |

### 3.1 练习1
 - 输入三个数，输出三个数中的最大值

```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
	int a, b, c;
	cin >> a >> b >> c;

	if(a > b && a > c) cout << a << endl;
	else if(b > a && b > c) cout << b << endl;
	else cout << c << endl;
	}
	return 0;
}
```

### 3.2 练习2
 - 用一条 if 语句，判断闰年

```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int mian()
{
	int year;
	cin >> year;
	
	if(year % 100 == 0 && year % 400 == 0 || year % 4 == 0 && year % 100 != 0) cout << "yes" << endl;
	else cout << "no" endl;
	}
}
return 0;
```

# 3 循环结构

## 1. while循环
 - 可以简单理解为循环版的if语句。if语句是判断一次，如果条件成立，则执行后面的语句；while是每次判断，如果成立，则执行循环体中的语句，否则停止

```cpp
include<iostream>
using namespace std;

int main()
{
	int i = 0;
	while(i < 10)
	{
		cout << i << endl;
		i++;
	}
	return 0;
}
```
### 1.1 练习1 立方和
 - 求1~100中所有数的立方和

```cpp
include<iostream>
using namespace std;

int main()
{
	int i = 1, sum = 0;
	while(i <= 100)
	{
		sum += i*i*i;
		i++;
	}
	cout << sum << endl;
	return 0;
}
```
### 1.2 练习2 斐波那契数列

 - 求斐波那契数列的第n项。f(1)=1, f(2)=1, f(3)=2, f(n)=f(n-1) + f(n-2)

```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
    int n;
    cin >> n;
    
    int a = 1,b = 1,i = 1;
    while(i < n)
    {
        int c = a + b;
        a = b;
        b = c;
        i ++;
    }
    //for(int i = 1;i<n;i++)
    cout << a << endl;
    return 0;
}
```
## 2. do while 循环
 - do while语句与while语句非常相似。唯一的区别是，do while语句限制性循环体后检查条件。不管条件的值如何，我们都要至少执行一次循环

```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
	int x = 1;
	while(x < 1)
	{
		cout << "x!" << endl;
		x ++;
	}
	int y = 1;
	do
	{
		cout << "y!" << endl;
	}while(y < 1);
	return 0;
}
```
## 3. for 循环
 - 基本思想：把控制循环次数的变量从循环体中剥离。
```cpp
for (init-statement : condition: expression)
{
    statement
}
```

 - init-statement可以是声明语句、表达式、空语句，一般用来初始化循环变量；
 - condition 是条件表达式，和while中的条件表达式作用一样；可以为空，空语句表示true
 - expression 一般负责修改循环变量，可以为空

```cpp
include<iostream>
using namespace std;

int main()
{
	for(int i = 0;i < 10; i++)
	{
		cout << i << endl;
	}
	return 0;
}
```
### 3.1 练习1
 - 求 1 * 9 + 2 * 8 + 3 * 7 + 4 * 6

```cpp
include<iostream>
using namespace std;

int main()
{
	int sum = 0;
	for(int i = 0，j = 10;i < j;i++,j--)
	{
		sum += i*j;
	}
	cout << sum << endl;
	return 0;
}
```
## 4. 跳转语句
### 4.1 break
 - 可以**提前从循环中退出，一般与if语句搭配**
 - 例题：判断一个大于1的数是否是质数

```cpp
include<iostream>
using namespace std;

int main()
{
	int n;
	cin >> n;
	
	bool is_prime = true;
	for(int i = 2; i < n; i++)
	{
		if(n % i == 0)
		{
			is_prime = false;
			break;
		}
	}
	if(is_prime) cout << "yes" << endl;
	else cout << "no" << endl;
	return 0;
}
```
### 4.2 continue
 - 可以**直接跳到当前循环体的结尾**。作用与if语句类似
 - 例题：求1~100中所有偶数的和
```cpp
include<iostream>
using namespace std;

int main()
{
	int sum = 0;
	for(int i = 0;i <= 100;i++)
	{
		if(i % 2 == 1) continue;
		sum += i;
	}
	cout << sum << endl;
	return 0;
}
```
## 5. 多层循环
```cpp
include<iostream>
using namespace std;

int main()
{
	for(int i = 0, k = 1;i <= 10;i++)
	{
		for(int j = 0;j < 10;j++, k++)
		{
			cout << k << ' ';
		}
		cout << endl;
	}
	return 0;
}
```
### 5.1 练习1
 - 打印1~100中的所有质数
```cpp
include<iostream>
using namespace std;

int main()
{
	for(int i = 2;i <= 100;i++)
	{
		bool is_prime = true;
	    for(int j = 2; j < i; j++)
		{
			if(i % j == 0)
			{
				is_prime = false;
				break;
			}
		}
		if(is_prime) cout << i << endl;
	}
	return 0;
}
```
### 5.2 练习2
 - 输入一个n，打印n阶菱形。n是奇数
 - n = 9 时的结果：
![在这里插入图片描述](https://img-blog.csdnimg.cn/80900d41eaed4fe88a1518718d76a43b.png)
```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
    int n;
    cin >> n;
    int cx = n/2,cy = n/2;
    for(int i = 0;i < n;i++)
    {
        for(int j = 0;j < n;j++)
        {
            if(abs(i-cx) + abs(j-cy) <= n/2)//只适用于奇数
                cout<<"*";
            else 
                cout<<' ';
        }
        cout<<endl;
    }
    return 0;
}
```

# 4 数组

## 1. 一维数组
### 1.1 数组的定义
 - 数组的定义方式和变量类似

```cpp
#include<iostream>
#include<algorithm>
using namespace std;

int main()
{
	int a[10], b[20];
	float f[33];
	double d[123];
	char c[21];
	
	return 0;
}
```

### 1.2 数组的初始化
 - 在main函数内部，未初始化的数组中的元素是随机的

```cpp
#include<iostream>
#include<algorithm>
using namespace std;

int main()
{
	int a[3] = {0,1,2};// 含有3个元素的数组
	int b[] = {0,1,1};// 维度是3的数组
	int c[5] = {0,1,2};// 等价于c[] = {0,1,2,0,0}
	char d[3] = {'a','b','c'};// 字符数组的初始化
	return 0；
}
```

### 1.3 访问数组元素(下标访问数组)
![在这里插入图片描述](https://img-blog.csdnimg.cn/ac6cb25b62704685beb3696d9eac31e5.png)
### 1.4 练习1 斐波那契数列
 - 使用数组实现求斐波那契数列的第N项

```cpp
#include<iostream>
#include<algorithm>
using namespace std;

int main()
{
    int n;
    int f[100];
    cin >> n;
    
    f[0] = 0, f[1] = 1;
    for(int i = 2; i <= n; i++)
    {
    	f[i] = f[i - 1] + f[i - 2];
    }
    cout << f[n] << endl;
    return 0;
}
```
### 1.5 练习2 倒排序
 - 输入一个n，再输入n个整数，将这n个整数逆序输出

```cpp
#include<iostream>
#include<algorithm>
using namespace std;

int main()
{
	int n;
	int a[100];
	
	cin >> n;
	for(int i = 0;i < n; i++) cin >> a[i];// 输入n个整数
	for(int i = n - 1; i >= 0; i--) cout << a[i] << ' ';
	cout << endl;
	return 0;
}
```
### 1.6 练习3 数组旋转
 - 输入一个n，再输入n个整数。将这个数组顺时针旋转k(k <= n)次，最后将结果输出。

```cpp
#include<iostream>
#include<algorithm>
using namespace std;

int main()
{
	int n,k;
	int a[100];
	
	cin >> n >> k;
	for(int i = 0; i < n; i++) cin >> a[i];
	
	reverse(a, a + k);
	reverse(a + k,a + n);
	reverse(a, a + n);

	for(int i = 0; i < n; i++) cout << a[i] << ' ';
	cout << endl;
	return 0; 
}
```
### 1.7 练习4 顺序输出
 - 输入n个数，将这n个数按从小到大的顺序输出

```cpp
#include<iostream>
#include<algorithm>
using namespace std;

int main()
{
	int n,k;
	int a[100];
	
	cin >> n >> k;
	for(int i = 0; i < n; i++) cin >> a[i];
	
	for(int i = 0; i < n; i++)
		for(int j = i + 1; j < n; j++)
			if(a[i] > a[j])
				swap(a[i],a[j]);

	for(int i = 0; i < n; i++) cout << a[i] << ' ';
	cout << endl;
	return 0; 
}
```
### 1.8 练习5 难题
 - 计算2的N次方，N <= 10000
![在这里插入图片描述](https://img-blog.csdnimg.cn/e709b540b8ff4f79b517bc9dceea3875.png)

```cpp
#include<iostream>
using namespace std;

const int N = 3010;

int main()
{
    int a[N] = {1};
    int n;
    cin >> n;
    int m = 1;
    
    for(int i = 0;i < n;i++)
    {
        int t = 0;
        for(int j = 0;j < m; j++)
        {
            t += a[j]*2;
            a[j]=t%10;
            t/=10;
        }
        if (t) a[m++] = 1;
    }
    for(int i =m-1;i>=0;i--)cout << a[i];//从最高位输出
    return 0;
}
```

## 2. 多维数组
 - int a[3][4]：大小为3的数组，每个元素是含有4个整数的数组。
 - int arr[10][20][30] = {0}; 将所有元素初始化为0，大小为10的数组，它的每个元素是含有4个整数的数组，这些数组的元素是含有30个整数的数组

![在这里插入图片描述](https://img-blog.csdnimg.cn/6ccb7b79117f4ee4802cd52174565e20.png)

### 2.1 练习1 回字形
 - 输入一个n行m列的矩阵，从左上角开始将其按回字形的顺序顺时针打印出来。

![在这里插入图片描述](https://img-blog.csdnimg.cn/1f42087171364b8caefdc8907ed79359.png)

# 5 字符串(重难点)

## 1. 字符与整数联系 — ASCII码
 - 每个常用字符都对应一个-128~127的数字，二者之间可以相互转化
```cpp
#include <iostream>
using namespace std;
int main()
{
	char c = 'a';
	cout << (int)c << endl;
	
	int a = 66;
	cout << (char)a << endl;
	return 0;
}
```
 - 常用ASCII值：’A’-‘Z’ 是65~90，’a’-‘z’是97-122，’0’-‘9’是48-57
 - 字符可以参与运算，运算时会将其当做整数：

```cpp
#include <iostream>
using namespace std;

int main()
{
	int a = 'B' - 'A';// 1
	int b = 'B' * 'A';// 4290
	char c = 'A' + 2;// C
	cout << a << endl;
	cout << b << endl;
	cout << c << endl;
	return 0;
}
```
### 1.1 练习1 统计数字和字母个数
 - 输入一行字符，统计出其中数字字符的个数，以及字母字符的个数

```cpp
#include<iostream>
using namespace std;

int main()
{
    char c;
    
    int nums = 0, chars = 0;// 数字和字母个数
    while(cin >> c)// 读入字符
    {
        if(c >= '0'&&c <= '9') nums++;
        else if(c >= 'A' && c <= 'z' || c >= 'a'&& c <= 'z') chars++;
    }
    printf("numbers:%d\nchars:%d",nums,chars);
    return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/6a343f65848d4e9c892b822e3d88adfc.png)
### 1.2 练习2 字符和数字的转换

```cpp
#include<iostream>
using namespace std;

int main()
{
    char c = 'a';
    cout << (int)c << endl;// 97
    printf("%d\n",'z'-'a');// 25
    printf("%c\n",'a'+3);// d
    
    int a ='B'-'A';
    char b = 'A'+2;
    cout << a << endl;// 1
    cout << b << endl;// C
    return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/566f974dca6041cf9a94d0fd14a40087.png)
### 1.3 练习3 查询ASCII码
```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
    for(int i = 1;i < 128;i++)
    printf("%d:%c\n",i,(char)i);// 输出ASCII码以及对应字符
    return 0;
}
```
## 2. 字符数组 — 字符数组存储字符串
 - **字符串就是字符数组加上结束符’\0'**，string底层就是用字符数组实现的。**存长度为L的字符串，则相应的字符数组长度至少为 L+1**。字符数组的长度大于字符串的长度，字符串实际长度为L+'\0'
 - 可以使用字符串来初始化字符数组，但此时要注意，每个字符串结尾会暗含一个’\0’字符，**因此字符数组长度至少要比字符串长度多1**
 - C语言约定：**如果字符型（char）数组的末尾包含了空字符\0(即0)，那么该数组中的内容就是一个字符串。string对象都是以’\0’结尾的，string是C++风格字符串**

![C风格字符串](E:\BaiduSyncdisk\C++学习\B站C++学习\1.C++学习\0.系统学习C++\系统学习C++笔记图片\C风格字符串.png)

- **因为字符串需要用0结尾，所以在声明字符数组的时候，要预留多一个字节用来存放0**

```cpp
#include <iostream>
using namespace std;

int main()
{
	// a1不是字符串，a2和a3都是字符串，因为都有'\0'
	char a1[] = {'C', '+', '+'}; // 列表初始化，没有空字符
	char a2[] = {'C', '+', '+', '\0'}; // 列表初始化，含有显示的空字符，有\0，可以被称为字符串
	char a3[] = "C++"; // 自动添加表示字符串结尾的空字符，数组长度为4，因为有'\0'字符。
	char a4[6] = "Daniel"; // 错误，没有空间可存放空字符，方框里至少填7
	cout << a2 << endl;
	printf("%s\n",a3);// 使用%s字符串类型，%c是单字符类型
	return 0;
}
```
另一个示例

```
char name[11];//可以存放10个字符，没有初始化，里面是垃圾值
char name[11] = "hello";// 初始内容为hello，系统会自动添加0
char name[]  = { "hello" };// 初始内容为hello，系统会自动添加0，数组长度是6
char name[11] = { "hello" };// 初始内容为hello，系统会自动添加0
char name[11]  { "hello" };// 初始内容为hello，系统会自动添加0。C++11标准
char name[11] = { 0 };  //把全部的元素初始化为0
```

### 2.1 字符数组读入fgets和getline和输出printf(重点)

 - **fgets()函数能读入空格**
 - **cin >> str; 输入字符串时，遇到空格或者回车就会停止**
 - **cout << str << endl; 输出字符串时，遇到空格或者回车不会停止**

```cpp
#include<iostream>
using namespace std;

int main()
{
	char str[100];
	cin >> str; // 输入字符串时，遇到空格或者回车就会停止
	cout << str << endl; // 输出字符串时，遇到空格或者回车不会停止
	printf("%s\n",str);// 等价于puts(str);puts函数后面包括换行符，printf不包括换行符
	return 0;
}
```
- **printf("%s\n",str); 等价于 puts(str)，但是puts函数后面包含换行符，printf输出不包含换行符**
```cpp
#include<cstdio>
#include<iostream>
using namespace std;

int main()
{
	char str[100];
	scanf("%s",str);// 输入字符串时，遇到空格或者回车就会停止
	printf("%s\n",str);// 等价于puts(str);puts函数包括换行符,printf函数不包括换行符
	return 0;
}
```
 - 读入一行字符串，包括空格，不能使用gets函数，已经被淘汰了。以下读入有空格的句子方法
 - 方式1：**使用fgets()函数**

```cpp
#include <iostream>
using namespace std;

int main()
{
	char str[100];
	fgets(str,100,stdin);// stdin是系统定义好的变量
	cout << str << endl;
	return 0;
}
```
[Acwing 815.打印字符串，这道题重点看](https://www.acwing.com/problem/content/817/)

```cpp
#include<iostream>
#include<cstring>
#include<cstdio>
using namespace std;

void print(char str[])
{
    // puts(str);// 调用函数直接打印，puts函数会输出回车
    printf("%s",str);// printf函数不会输出回车(换行符)
}

int main()
{
    char str[110];
    // 多输入一个回车，所以中间是101
    fgets(str,101,stdin);// 在字符串最后加回车"\n",使用puts函数会输出回车，printf不会输出回车
    
    // 或者直接用getline
    cin.getline(str, 101);// getline函数和fgets函数二者选择其中一个
    print(str);
    return 0;
}
```

 - 方式2：**使用getline函数**——只适用于string类型

```cpp
#include<iostream>
#include<string>
using namespace std;

int main()
{
	string str;
	getline(cin, str);// 只能是string类型
	cout << str << endl;
	return 0;
```
#### 2.1.1 练习1 字符数组输出printf
```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
    char a1[] = {'A','B','C'};
    cout << a1 + 1 << endl;// 输出BC
    // 从A开始输出， cout << a1 << endl
    // 从B开始输出， cout << a1 + 1 << endl
    char a2[] = {"ABCDEF"};
    printf("%s\n",a2 + 2);// 输出cdef
}
```
#### 2.1.2 练习2 字符数组读入scanf(难点)

 - **cin函数遇到空格、回车、结束符就停止读入**
 - **scanf("%s",a)一定不要加&**
 - **所有数组的名字本身就是一个指针**
 - 字符数组char可以用cin或者scanf，但是字符串string只能用cin

```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
    char s[100];
    // scanf("%s",s); 输入abc
    // cout << s << endl;// 输出abc
    cin >> s;// 同scanf，输入字符串时，遇到空格或者回车就会停止
    cout << s << endl;
    return 0;
}
```
 - 从指定数组位置开始输入和输出数据
```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
	char s[100];
	// 读入字符串是读到空格或者回车为止。
    cin >> s+1;// 从s[1]开始读入字符串，就是从s[1]开始存入字符串abc,相配套的是cout << s+1,从s[1]开始输出字符串。
    // scanf("%s",s+1);// 不要用取地址符号&，或者scanf("%s",&s[1])也是可以的,这里也是从s[1]开始存入字符串，同上面的 cin >> s+1
    
    cout << s+1 << endl;// 从s[1]开始输出完整字符串，abc
    cout << s[1] << endl; // 数组下标从1开始，结果为a。
    // printf("%s\n",s + 1); 表示从下表1开始输出。等同于cout << s+1 <<endl
    return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/135638847bb74ba5bfe892d610f1f3ab.png)

```cpp
#include<iostream>
#include<cstdio>
using namespace std;

int main()
{
	char s[100];
	scanf("%s",s + 2);
	cin >> s + 2;
	printf("%s", s + 1);
	cout << s + 2 << endl;
	return 0;
}
```

### 2.2 字符数组的常用操作\<cstring>(难点)
 - 下面几个函数需要引入头文件：#include <string.h>
 - strlen(str)，**字符串的长度，只计算字符串中的元素，不包括\0**
 - strcmp(a, b)，比较两个字符串的大小，a < b 返回-1，a == b 返回0，a > b返回1。这里的比较方式是**字典序**！
 - strcpy(a, b)，将字符串b复制给从a开始的字符数组

```cpp
#include<iostream>
#include<cstdio>
#include<cstring>
using namespace std;

int main()
{
	char a[100] = "hello world!", b[100];
	cout << strlen(a) << endl;// 不包括'\0'字符，12
	strcpy(b, a);// 复制
	return 0;
}
```
- strcpy复制函数

```cpp
#include<iostream>
#include<cstdio>
#include<cstring>
using namespace std;

int main()
{
	char s1[100], s2[100];
	scanf("%s",s1);
	strcpy(s2, s1);// 读入s1复制给s2，
	cout << s2 << endl;
	return 0;
}
```
 - strcmp 比较函数
```cpp
#include<iostream>
#include<cstdio>
#include<cstring>
using namespace std;

int main()
{
	char a[100], b[100];
	scanf("%s%s",a,b);
	cout << strcmp(a,b) << endl;// 输入时两个字符串需要用空格或者回车分开
	return 0;
}
```
- 遍历每一个字符

```cpp
#include<iostream>
#include<cstdio>
#include<cstring>
using namespace std;

int main()
{
	char s1[100], s2[100];
	scanf("%s",s1);
	int len = strlen(s1);// 提高效率
	for(int i = 0; i < len; i++) cout << s1[i] << endl;
	return 0;
}
```

#### 2.2.1 练习1 字符数组(char)长度strlen()
- **char 数组求长度用strlen函数, int 数组用siezof(a)/sizeof(a[0]), string类型用size()函数**
```cpp
#include<iostream>
#include<cstring>
#include<cstdio>
using namespace std;

int main()
{
	// 第一种方法
    char s[100];
    scanf("%s",s);// cin >> s
    cout << strlen(s) << endl;// 长度
    return 0；
    
    // 第二种方法
    char s[100];
    scanf("%s",s);
    
    int len = 0
    for(int i = 0; s[i] ;i++) len++;// s[i]表示不等于零的情况下，i++，字符串最后是'\0'
    
    cout << len << endl;
}
```
#### 2.2.2 练习2 字符串比较strcmp()
```cpp
#include<iostream>
#include<cstring>
#include<cstdio>
using namespace std;

int main()
{
    char s1[100],s2[100];
    scanf("%s%s",s1,s2);   
    cout << strcmp(s1,s2) << endl;// 字符串的比较
    return 0;
}
```
#### 2.2.3 练习3 字符串复制strcpy()

```cpp
#include<iostream>
#include<cstring>
#include<cstdio>
using namespace std;

int main()
{
    char s1[100],s2[100];
    scanf("%s",s1);  
    strcpy(s2,s1);  
    cout << s2 << endl;//字符串复制  
    return 0;
}
```
#### 2.2.4 练字4 遍历字符数组中字符strlen()
```cpp
#include<iostream>
#include<string.h>
using namespace std;

int main()
{
	char a[100] = "hello world!";
	// for(int i = 0;i < strlen(a);i++) cout << a[i] << endl;// 这种写法效率低
	for(int i = 0, len = strlen(a);i < len; i++) cout << a[i] << endl;// 效率高，需要提前strlen长度算出来
	return 0;
}
```
### 2.3 练习1 Acwing 772.只出现一次的字符
 [Acwing 772.只出现一次的字符](https://www.acwing.com/problem/content/774/)
 - 题目要求：给定一个只包含小写字母的字符串，请你找到第一个仅出现一次的字符。如果没有，输出“no”。
 - 思路：如何读入字符串？如何遍历字符串中每个字符？如何统计每个字符出现的次数？
 - 如何统计字母出现的次数：开一个cnt[26]数组

 - 方法1：不使用len = strlen()函数

```cpp
#include<iostream>
#include<cstdio>
#include<cstring>// 字符串的函数
using namespace std;

int cnt[26] = {0};// 存储每个字母出现的次数
char str[100010];// 存储字符串

int main()
{
    cin >> str;
    // str[i]里面都是小写字母，小写字母 - 'a'结果是整数，0-25分别表示a-z，'a'在做运算时都是整数运算
    for(int i = 0;i < strlen(str);i ++) cnt[str[i] - 'a'] ++;// cnt[]++表示对当前数组元素进行自增操作，元素值+1。数组加上下标就是变量
    // strlen每次进行循环都会重新执行一遍，延长执行的时间
    
    for(int i = 0; i < strlen(str);i ++)
        if(cnt[str[i] - 'a'] == 1)// 判断cnt[]中哪一个的元素值为1
        {
            cout << str[i] << endl;// 只出现一次则输出字符
            return 0;
        }
    
    puts("no");// 没有则输出no
    return 0;
}
```
方法2：**使用len = strlen(str)，可以缩短运行时间**

```cpp
#include<iostream>
#include<cstdio>
#include<cstring>// 字符串的函数
using namespace std;

int cnt[26] = {0};// 存储每个字母出现的次数
char str[100010];// 存储字符串

int main()
{
    cin >> str;
    int len = strlen(str);
    // str[i]里面都是小写字母，小写字母 - 'a'结果是整数，0-25分别表示a-z，'a'在做运算时都是整数运算
    for(int i = 0;i < len;i ++) cnt[str[i] - 'a'] ++;// cnt[]++表示对当前数组元素进行自增操作，元素值+1。数组加上下标就是变量
    // strlen每次进行循环都会重新执行一遍，延长执行的时间
    
    for(int i = 0; i < len;i ++)
        if(cnt[str[i] - 'a'] == 1)// 判断cnt[]中哪一个的元素值为1
        {
            cout << str[i] << endl;
            return 0;
        }
    
    puts("no");
    return 0;
}
```
 - 方法3：**不求str的长度，条件用str[i]，表示遇到'\0'就停止。字符串结尾是\0**

```cpp
#include<iostream>
#include<cstdio>
#include<cstring>// 字符串的函数
using namespace std;

int cnt[26] = {0};// 存储每个字母出现的次数
char str[100010];// 存储字符串

int main()
{
    cin >> str;
    // str[i]里面都是小写字母，小写字母 - 'a'结果是整数，0-25分别表示a-z，'a'在做运算时都是整数运算
    for(int i = 0;str[i];i ++) cnt[str[i] - 'a'] ++;// cnt[]++表示对当前数组元素进行自增操作，元素值+1。数组加上下标就是变量。等价于 cnt[] += 1    
    for(int i = 0;str[i];i ++)
        if(cnt[str[i] - 'a'] == 1)// 判断cnt[]中哪一个的元素值为1
        {
            cout << str[i] << endl;
            return 0;
        }
    
    puts("no");
    return 0;
}
```
### 2.4 练习2 Acwing 769.替换字符
[Acwing 769.替换字符](https://www.acwing.com/problem/content/771/)

 - 把一个字符串中特定的字符全部用给定的字符替换，得到一个新的字符串

**难点**
 - scanf("\n%c", &c);读入要替换的字符，读入字符不会自动过滤掉前面的回车\n，会读入回车。需要在前面加\n

```cpp
#include<cstdio>
#include<iostream>
using namespace std;

int main()
{
    char str[31];
    scanf("%s",str);// 读入到回车或者'\0'就结束
    
    char c;// 读入要替换的字符
    scanf("\n%c", &c);// 读入要替换的字符，读入字符不会自动过滤掉前面的回车\n，会读入回车。需要在前面加\n，过滤回车。cin 没有这个问题
    
    for(int i = 0;str[i];i++)
        if(str[i] == c)
           str[i] = '#';
    
    puts(str);
    return 0;
}
```
## 3. 标准库类型string — 用string存储字符串
 - 可变长的字符序列，比字符数组更加好用。需要引入头文件：#include \<cstring>
### 3.1 定义和初始化
```cpp
#include<iostream>
#include<cstring>
#include<cstdio>
using namespace std;

int main()
{
	string s1; // 默认初始化，s1是一个空字符串
	string s2 = s1; // s2是s1的副本
	string s3 = "hiya";// s3是该字符串字面值的副本
	string s4(10, 'C'); // s4内容是ccccccccccc
	return 0;
}
```
### 3.2 string 的操作
#### 3.2.1 string的读入cin和输出puts(重点)
```cpp
#include<iostream>
#include<string>
using namespace std;

int main()
{
	string s1,s2;
	cin >> s1 >> s2;// 读入字符串
	// scanf("%s",&s1);是错误的写法，不能用scanf读入字符串
	cout << s1 << ' ' << s2 << endl;
	// 输出可以用printf, 
	printf("%s\n",s1.c_str());// c_str()是成员函数，返回的是存储字符串s1的字符数组的首地址,打印出的结果是字符数组。cin输入abc,打印出来的也是abc
	// 输出也可以用puts
	puts(s1.c_str());
	return 0;
}
```
 - 注意：**不能用printf直接输出string，需要写成：printf(“%s”, s.c_str())**
#### 3.2.2 string读入一行使用getline(重点)
 - 如果输入是：abc cde abd，使用 cin >> s，则输出是abc，使用 getline(cin, s)则 输出是abc cde abd。

```cpp
#include<iostream>
#include<cstring>
using namespace std;

int main()
{
	string s1;
	getline(cin, s1);// string读入一行
	// cin >> s1; // 表示读入第一个字符串
	// cin.getline(s2, 1000);// 字符串使用cin读入一行
	cout << s1 << endl;
	return 0;
}
```
#### 3.2.3 string的empty和size(长度)函数
 - 注意size是无符号整数，因此 s.size() <= -1一定成立。
 - empty()返回的是bool值

```cpp
#include<iostream>
#include<cstring>
using namespace std;

int main()
{
	string s1, s2 = "abc";
	cout << s1.empty() << endl;// empty返回的是布尔值
	cout << s2.empty() << endl;
	cout << s2.size() << endl;
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/ffa430d704a14dfb831ba41f5b268ba9.png)

#### 3.2.4 string的比较
 - 支持 > < >= <= == !=等所有比较操作，按字典序进行比较

#### 3.2.5 string对象赋值
```cpp
string s1(10, ‘c’), s2;		// s1的内容是 cccccccccc；s2是一个空字符串
s1 = s2;					// 赋值：用s2的副本替换s1的副本
							// 此时s1和s2都是空字符串
```
#### 3.2.6 两个string对象相加
```cpp
string s1 = “hello,  ”, s2 = “world\n”;
string s3 = s1 + s2;					// s3的内容是 hello, world\n
s1 += s2;								// s1 = s1 + s2
```
#### 3.2.7 字面值和string对象相加
 - 做加法运算时，**字面值和字符都会被转化成string对象**，因此**直接相加就是将这些字面值串联起来**。

```cpp
#include<iostream>
#include<cstring>
using namespace std;

int main()
{
	string s1 = "hello", s2 = "world";		// 在s1和s2中都没有标点符号
	string s3 = s1 + ", " + s2 + '\n';
	cout << s3 <<endl;
	return 0;
}
```
 - 当把string对象和字符字面值及字符串字面值混在一条语句中使用时，必须确保**每个加法运算符的两侧的运算对象至少有一个是string**
```cpp
string s4 = s1 + ",";	// 正确：把一个string对象和有一个字面值相加
string s5 = "hello" + ","; // 错误：两个运算对象都不是string
string s6 = s1 + "," + "world";  // 正确，每个加法运算都有一个运算符是string。s1 + ","结果是string类型
string s7 = "hello" + "," + s2;  // 错误：不能把字面值直接相加，运算是从左到右进行的。先计算"hello" + ","得到字符串，不是string类型
```
### 3.3 处理string对象中字符(重点)
#### 3.3.1 数组长度(char-strlen&string-size)+引用&
 - 可以**将string对象当成字符数组来处理**
 - **char字符数组长度用strlen()**
 - **string字符串长度使用size()**

```cpp
#include<iostream>
#include<string.h>
using namespace std;

int main()
{
	// char a[100] = "hello world!";
	// for(int i = 0;i < strlen(a);i++) cout << a[i] << endl; 
	string s = "hello world";
	for(int i = 0;i < s.size();i ++) cout << s[i] << ' ';
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/97ebc4e63390455081e64a68f5a1a64d.png)
 - 或者**使用基于范围的for语句**

```cpp
#include<iostream>
#include<cstring>
using namespace std;

int main()
{
	string s = "hello world";
	for(char c : s) cout << c << endl;// c++的范围遍历，char 表示每一个字符数组元素的类型，s表示字符串，c顺次遍历s[0]，s[1],...
	cout << endl;
	cout << s << endl;
	
	for(char &c : s) c = 'a';// 改变c的同时改变s的值，加了&表示c等价于字符串s
	cout << s << endl;
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/e2680ca3a5cb49b1abbddf1ebcd059c7.png)

```cpp
int main()
{
	string s = "hello world";
	for(char c : s)
	{
		c = 'a';
	}

	// 等价于下面的操作
	for(int i = 0; i < s.size();i ++)
	{
		char c = str[i];
		c = 'a';
	}
}
```
- 加引用符号&

```cpp
int main()
{
	string s = "hello world";
	for(char &c : s)
	{
		c = 'a';
	}

	// 等价于下面的操作
	for(int i = 0; i < s.size();i ++)
	{
		char &c = str[i];// 加引用符号&后，c和str完全相同
		c = 'a';
	}
}
```
#### 3.3.2 auto语法
- auto让编译器自己猜数据类型
```cpp
#include<iostream>
#include<cstring>
using namespace std;

int main()
{
	string s = "hello world";
	for(auto c : s) cout << c << endl;// c++的范围遍历，char 表示每一个字符数组元素的类型，s表示字符串，c顺次遍历s[0]，s[1],...
	return 0;	
}
```
#### 3.3.3 练习1 Acwing 767. 信息加密
[Acwing 767.信息加密](https://www.acwing.com/problem/content/769/)
 - 密码翻译，输入一个只包含小写字母的字符串，将其中的每个字母替换成它的后继字母，如果原字母是’z’，则替换成’a’。
 - 思考：读入包括空格的字符串(使用getline函数)

```cpp
#include<iostream>
using namespace std;

int main()
{
    string s;
    getline(cin, s);// 读入有空格的字符串
    
    for(auto &c : s)
    {
        if(c >= 'a' && c <= 'z') c = 'a' + (c - 'a' + 1) % 26;// 后面表示新的偏移量
        else if(c >= 'A' && c <= 'Z') c = 'A' + (c - 'A' + 1) % 26;
    }
    
    cout << s << endl;
    return 0;
}
```

# 6 函数

## 1. 函数基础

 - 一个典型的函数定义包括以下部分：返回类型、函数名字、由0个或多个形参组成的列表以及函数体
 - void 表示没有返回值

```cpp
#include<iostream>
using namespace std;

// 函数声明
int foo(int n);

// 函数定义
int foo(int n)
{
	int res = 0;
	for(int i = 0;i < n; i++)
	{
		res *= i;
	}
	return res;
}

int main();
{
	int t = foo(5);
	cout << t << endl;
	return 0;
}
```

### 1.1 编写函数
 - 我们来编写一个求阶乘的程序，程序如下所示：

```cpp
int fact(int val)
{
    int ret = 1;
    while (val > 1)
        ret *= val -- ;
    return ret;
}
```
 - 返回类型是int，函数名字是fact，它作用于一个整型参数，返回一个整型值
 - return语句负责结束fact并返回ret的值

### 1.2 调用函数

```cpp
int main()
{
    int j = fact(5);
    cout << "5! is " << j << endl;
    return 0;
}
```
 - 函数的调用完成两项工作：一是用实参初始化函数对应的形参，二是将控制权转移给被调用函数。此时，主调函数的执行被暂时中断，被调函数开始执行

### 1.3 形参和实参

 - **实参是形参的初始值**。第一个实参初始化第一个形参，第二个实参初始化第二个形参，依次类推。形参和实参的类型和个数必须匹配

```cpp
fact(“hello”);		// 错误：实参类型不正确
fact(); 			// 错误：实参数量不足
fact(42, 10, 0); 	// 错误：实参数量过多
fact(3.14); 		// 正确：该实参能转换成int类型，等价于fact(3);
```

 - 形参也可以设置默认值，但所有默认值必须是最后几个。当传入的实参个数少于形参个数时，最后没有被传入值的形参会使用默认值

### 1.4 函数的形参列表
 - 函数的形参列表可以为空，但是不能省略
```cpp
void f1() {/* …. */}			// 隐式地定义空形参列表
void f2(void) {/* … */} 		// 显式地定义空形参列表
```
 - 形参列表中的形参通常用逗号隔开，其中每个形参都是含有一个声明符的声明。即使两个形参的类型一样，也必须把两个类型都写出来：
```cpp
int f3(int v1, v2) {/* … */} 		// 错误
int f4(int v1, int v2) {/* … */} 	// 正确
```
### 1.5 函数返回类型
 - 大多数类型都能用作函数的返回类型。一种特殊的返回类型是void，它表示函数不返回任何值。函数的返回类型不能是数组类型或函数类型，但可以是指向数组或者函数的指针

### 1.6 局部变量、全局变量与静态变量
 - **局部变量只可以在函数内部使用，全局变量可以在所有函数内使用**。当局部变量与全局变量重名时，会优先使用局部变量
 - **static静态变量相当于在该函数内部开了一个只有该函数能使用的全局变量**
![在这里插入图片描述](https://img-blog.csdnimg.cn/fe8f9cc56e1d411b82a159970d7d3931.png)

## 2. 参数传递
### 2.1 传值参数
 - 当初始化一个非引用类型的变量时，初始值被拷贝给变量。此时，对变量的改动不会影响初始值

```cpp
#include<iostream>
using namespace std;

int f(int x)
{
	x = 5;
}
int main()
{
	int x = 10;
	f(x);
	cout << x << endl;
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/2966428459044d52ad8f0b97a0fd00fd.png)

### 2.2 传引用参数(可以改变实参)
 - **当函数的形参为引用类型时，对形参的修改会影响实参的值**。使用引用的作用：**避免拷贝、让函数返回额外信息**

```cpp
#include<iostream>
using namespace std;

int f(int &x)
{
	x = 5;
}
int main()
{
	int x = 10;
	f(x);
	cout << x << endl;
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/66eb46f1a2124205bb5c6a56825a2344.png)

### 2.3 数组形参(可以修改函数外数组)
 - 在函数中对数组中的值的修改，会影响函数外面的数组
#### 2.3.1 一维数组形参
```cpp
// 尽管形式不同，但这三个print函数是等价的
void print(int *a) {/* … */}
void print(int a[]) {/* … */}
void print(int a[10]) {/* … */}
```
 - 实例
```cpp
#include<iostream>
using namespace std;

void print(int a[])
{
	for(int i = 0; i < 10; i ++) cout << a[i] << endl;
}
int main()
{
	int a[10];
	for(int i = 0; i < 10; i ++) a[i] = i;
	print(a);
	return 0;
}
```

 - 传入数组

![在这里插入图片描述](https://img-blog.csdnimg.cn/da8681e976df4eb1b33a6c79a0b2192d.png)

- 传入指针

![在这里插入图片描述](https://img-blog.csdnimg.cn/2b2488eb938e44fc966e96ed721561a8.png)

#### 2.3.2  多维数组形参
```cpp
// 多维数组中，除了第一维之外，其余维度的大小必须指定
void print(int (*a)[10]) {/* … */}
void print(int a[][10]) {/* … */}
```

```cpp
#include<iostream>
using namespace std;

void print(int a[][10])// 第1个参数可以省略，第2个不能省
{
	for(int i = 0; i < 10; i ++)
	{
		for(int j = 0; j < 10; j ++)
			cout << a[i][j] << ' ';
		cout << endl;
	}
}
int main()
{
	int a[10][10];
	for(int i = 0; i < 10; i ++)
	{
		for(int j = 0; j < 10; j ++)
			a[i][j] = j;
	}
	print(a);
	return 0;
}
```
 - 改变函数内数组元素，从而改变函数外数组的元素

```cpp
#include<iostream>
using namespace std;

void output(int n, int m, int a[][3])// 第1个参数可以省略，第2个不能省
{
	for(int i = 0; i < n; i ++)
	{
		for(int j = 0; j < m; j ++)
		{
			cout << a[i][j] << ' ';
			a[i][j] = 1;
		}
		cout << endl;
	}
}
int main()
{
	int a[3][3] = {{1,2,3},{4,5,6},{7,8,9}};
	output(3,3,a);
	puts("");
	for(int i = 0; i < 3; i ++)
	{
		for(int j = 0; j < 3; j ++)
		{
			cout << a[i][j] << ' ';
		}
		cout << endl;
	}
	
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/a2c0fb64190140a6bdf0bdf68f656a33.png)

- 未传入foo(5)返回的是5，10；如果是foo(5,3) 返回的是5，3

![在这里插入图片描述](https://img-blog.csdnimg.cn/6ef71d818afb47baadc4b4eb7ea53f36.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/0d49c964dfb74f4ebf3883d651663e1f.png)

 - **默认的值必须是后面连续的几个参数，加入foo(int a = 10,int b)则会报错**

### 2.4 函数重载
- 函数名一样，需要参数类型不同（函数名和参数类型不能都一样）

![在这里插入图片描述](https://img-blog.csdnimg.cn/4cc99d5d241448228959a9da8ba1abab.png)

### 2.5 数组大小
![在这里插入图片描述](https://img-blog.csdnimg.cn/956afbbc4fcd49fc95840dbe2fd498af.png)
 - 结果
![在这里插入图片描述](https://img-blog.csdnimg.cn/9339e074febf45d6b038a0ed74584329.png)
 - 64位系统，指针长度都是64位，就是8个字节，所以b的大小为8

## 3. 返回类型和return语句
 - return 语句终止当前正在执行的函数并将控制权返回到调用该函数的地方
 - return语句有两种形式：
```cpp
return;
return expression;
```
### 3.1 无返回值函数
 - 没有返回值的return语句只能用在返回类型是void的函数中。返回void的函数不要求非得有return语句，因为在这类函数的最后一句后面会隐式地执行return
 - 通常情况下，void函数如果想在它的中间位置提前退出，可以使用return语句。return的这种用法有点类似于我们用break语句退出循环
```cpp
void swap(int &v1, int &v2)
{
    // 如果两个值相等，则不需要交换，直接退出
    if (v1 == v2)
        return;
    // 如果程序执行到了这里，说明还需要继续完成某些功能
    
    int tmp = v2;
    v2 = v1;
    v1 = tmp;
    // 此处无须显示的return语句
}
```

### 3.2 有返回值的函数
 - 只要函数的返回类型不是void，则该函数内的每条return语句必须返回一个值。return语句返回值的类型必须与函数的返回类型相同，或者能隐式地转换函数的返回类型 

```cpp
#include<iostream>
using namespace std;

int max(int x, int y)
{
	if(x > y) return x;
	return y;
}

int main()
{
	int x, y;
	cin >> x >> y;
	cout << max(x, y) << endl;
	return 0;
}
```

## 4. 函数递归(重难点)
 - 在一个函数内部，也可以调用函数本身

```cpp
#include<iostream>
using namespace std;

int fact(int n)
{
	if(n <= 1) return 1;
	return n * fact(n - 1);
}

int main()
{
	int n;
	cin >> n;
	cout << fact(n) << endl;
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/b188da44291e4d9d877e7f078b739830.png)
- 函数嵌套

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/7b316e5fcb2b42acbe72c26e6ef092d1.png)
 - 结果
![在这里插入图片描述](https://img-blog.csdnimg.cn/8d0df1bdb8574a879e0b6ac73eed1ef6.png)
 - 调用过程
![在这里插入图片描述](https://img-blog.csdnimg.cn/893c760880ef4815aeb1579a36b3b374.png)

# 7 类、结构体、指针、引用

## 1. 类和结构体

### 1.1 类的定义
```cpp
class Person
{
    private:
        int age, height;
        double money;
        string books[100];
    
    public:
        string name;// 变量
        
        void say()
        {
            cout << "I'm " << name << endl;
        }
        
        int get_age
        {
            return age;
        }

		void add_money(double x)// 函数
		{
			money += x;
		}
);
```
 - **类中的变量和函数**被统一称为**类的成员变量**
 - **private**后面的内容是**私有成员变量**，**在类的外部不能访问**；**public**后面的内容是**公有成员变量，在类的外部可以访问**

### 1.2 类的使用
```cpp
#include <iostream>
using namespace std;
const int N = 1000010;

class Person
{
    private:// 私有内容
        int age, height;
        double money;
        string books[100];
    
    public:// 公共内容
        string name;
        
        void say()
        {
            cout << "I'm " << name << endl;
        }
        
        int set_age(int a)
        {
            age = a;
        }
        
        int get_age()
        {
            return age;
        }
    
        void add_money(double x)
        {
            money += x;
        }
} person_a, person_b, persons[100];// 可以声明一个数组

int main()
{
	Person persons[100];
    Person c;
    
    c.name = "yxc";      // 正确！访问公有变量
    c.age = 18;          // 错误！访问私有变量
    c.set_age(18);       // 正确！set_age()是共有成员变量
    c.add_money(100);
    
    c.say();
    cout << c.get_age() << endl;
    
    return 0;
}
```
 - 结构体和类的作用是一样的。不同点在于类默认是private，结构体默认是public

### 1.3 结构体
 - 结构体和类的作用是一样的。不同点在于类默认是private，结构体默认是public

```cpp
struct Person
{
    private:
        int age, height;
        double money;
        string books[100];
		
		int get_height()
		{
			return height;
		}
    
    public:
        string name;
        
        void say()
        {
            cout << "I'm " << name << endl;
        }
        
        int get_age
        {
            return age;
        }

		void add_money(double x)
		{
			money += x;
		}
)person_a, person_b, persons[100];
```
### 1.4 构造函数
```cpp
#include <iostream>
using namespace std;

struct Person
{
	int age, height;
    double money;
	// 无参构造函数
	Person() {}

	Person (int _age. int _height) : age(_age), hight(_hight) {}
	
	// 有参构造函数
	Person(int _age, int _height, double _money)// 名称和结构体一样
	{
		age = _age;
		height = _height;
		money = _money;
	}

	// 另外一种赋值的方式
	Person(int _age, int _height, double _money) : age(_age), hight(_hight), money(_money){}
};// 一定加封号

int main()
{
	Person p;// 无参构造函数
	Person p(18, 180, 100.0);// 调用构造函数
	Person p = {18, 180, 100.0};
	return 0；
}
```

## 2. 指针和引用
### 2.1 指针
 - **指针指向存放变量的值的地址**，因此我们可以通过指针来修改变量的值

```cpp
#include<iostream>
using namespace std;

int main()
{
	int a = 10;
	int* p = &a;
	*p += 5;
	cout << *p << endl;
	return 0;
}
```
 - 通过指针修改变量的值
```cpp
#include<iostream>
using namespace std;

int main()
{
	int a = 10;
	int* p = &a;
	int** q = &p;// 求p本身的地址
	cout << q << endl;// 打印指针p的地址
	cout << *p << endl;// 10
	*p = 12;
	cout << *p << endl;// 12
	cout << a << endl;// 12，读取并修改变量的值
	return 0;
}
```

### 2.2 数组
 - **数组名是一种特殊的指针。指针可以做运算**

```cpp
#include<iostream>
using namespace std;

int main()
{
	int a[5] = {1,2,3,4,5};
	for(int i = 0; i < 5; i++) cout << *(a + i) << endl;
	return 0;
}
```

```cpp
#include<iostream>
using namespace std;

int main()
{
	char c;
	int a[5] = {1,2,3,4,5};
	
	int* p = &a[0], *q = &a[1];
	cout << q - p << endl;
	return 0;
}
```

 - 查询数组的地址void* &，十六进制

```cpp
#include<iostream>
using namespace std;

char a, b;

int main()
{
	char c;
	int a[5] = {1,2,3,4,5};

	cout << (void*)&c << endl;
	cout << a << endl;
	for(int i = 0;i < 5;i++)
		cout << (void*)&a[i] << endl;
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/2c7ac4ca8ff14b2382bf70d1e227f482.png)
 - 数组地址间隔4个字节，int型是4个字节
![在这里插入图片描述](https://img-blog.csdnimg.cn/b844fa2f607346fc91635f13818aeb23.png)
### 2.3 引用
 - 引**用和指针类似，相当于给变量起个别名**

```cpp
#include<iostream>
using namespace std;

int main()
{
	int a = 10;
	int &p = a;
	p += 5;
	cout << p << endl;
	return 0;
}
```

```cpp
#include<iostream>
using namespace std;

int main()
{
	int a = 10;
	int* p = a;// 指针
	int& p = a;// 引用，别名
	p += 5;
	cout << p << endl;
	return 0;
}
```
### 2.4 查询地址
```cpp
#include<iostream>
using namespace std;

int main()
{
	char c = 'a', b;// 局部变量定义在栈空间，全局变量定义在堆空间
	cout << (void*)&c << endl;
	cout << (void*)&b << endl;// 连续定义的变量，地址相邻
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/68430e3caead4250a6ab92e2086787ee.png)

## 3. 链表
![在这里插入图片描述](https://img-blog.csdnimg.cn/e647eef8275d49e7b90a20e92507ef24.png)

```cpp
#include<iostream>
using namespace std;

struct Node
{
	int val;
	Node* next;
	Node(int _val) : val(_val), next(NULL) {} // 默认构造函数，NULL说明是空指针
}*head;

int main()
{
	// 分别给链表结点赋值1,2,3
	Node* p = new Node(1);// new Node(1)表示定义一个Node类型的变量，返回的是变量的地址。加new返回的是地址，不加new返回的是值。生成一个结构体，结构体指针放在p里面
	Node* q = new Node(2);
	auto o = new Node(3);// auto 是自动判断类型是指针结点类型

	p->next = q;
	q->next = o;

	// 	添加结点4
	Node* u = new Node(4);
	u->next = head;// 将head赋值给u->next，
	head = u;// head头结点指向u

	// 删除结点1
	head->next = head->next->next;// 右边head->next是指1

	// 遍历链表中字符
	Node* head = p;// 头结点是p

	for(Node* i = head; i != 0; i = i->next)// i = 0时结束，i->next是指下一个结点
		cout << i->val << endl;// 输出的是值

	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/45eb5491824e4f8e8a0f81157e16ce12.png)
#### 3.1 添加结点
```cpp
Node* u = new Node(4);
u->next = head;// head赋值给u->next，指向head指向的节点
head = u;// head头结点指向u
```
 - u->next = head; head赋值给u->next，u->next指向head，这里的节点1就是head节点，head和节点1是等价的
![在这里插入图片描述](https://img-blog.csdnimg.cn/4121f53fa27c40f08d000b443fcecba6.png)
- head = u; 将结点u赋值给head，head指向u
![在这里插入图片描述](https://img-blog.csdnimg.cn/f2230279c1954b25aea303f4ef2d5fbf.png)
![在这里插入图片描述](https://img-blog.csdnimg.cn/1c1a14cfb70d47d9b37bc04835414d4e.png)
#### 3.2 删除结点
![在这里插入图片描述](https://img-blog.csdnimg.cn/62a64cc356b1463a9e052d2a0525d25f.png)

```cpp
// 删除结点1
head->next = head->next->next;// 右边head->next是指1，意思是是 head->next指向head->next->next，也就是4直接指向2
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/fabb69a288044ec78c58fb2f2724bcee.png)

# 8 STL、位运算和常用库函数

# STL

## 1. vector(尾部增删)	

 - vector是变长数组，支持随机访问，不支持在任意位置O(1)插入。为了保证效率，**元素的增删一般应该在末尾进行**

### 1.1 声明

```cpp
#include <vector> 	头文件
vector<int> a;		相当于一个长度动态变化的int数组
vector<int> b[233];	相当于第一维长233，第二位长度动态变化的int数组
a.size();// 长度
a.empty();// 返回的是bool值
a.clear();// 清空

struct rec
{
	int x, y;
};
vector<rec> c;		自定义的结构体类型也可以保存在vector中
```
### 1.2 长度size/判断是否为空empty
 - **size函数返回vector的实际长度（包含的元素个数）**
 - empty函数返回一个bool类型，表明vector是否为空。二者的时间复杂度都是O(1)
 - 所有的STL容器都支持这两个方法，含义也相同，之后我们就不再重复给出
### 1.3 清空clear
 - clear函数把vector清空
### 1.4 迭代器iterator
 - 类似**指针或者数组下标**的概念，**相当于地址**
 - **迭代器就像STL容器的“指针”**，**用星号“*”操作符解除引用**
 - 一个保存int的vector的迭代器声明方法为：
```cpp
vector<int>::iterator it = a.begin();// it + 2相当于访问a[2],it访问的就是a[0]
a.end();// 最后元素的下一个位置
*a.begin();// = a[0], *就是取值，a.begin()可以理解为指针
```
 - **vector的迭代器是“随机访问迭代器”**，可**把vector的迭代器与一个整数相加减，其行为和指针的移动类似**。可**把vector的两个迭代器相减**，结果**和指针相减类似**，**得到两个迭代器对应下标之间的距离**
### 1.5 遍历begin/end(重点)
 - **begin函数返回指向vector中第一个元素的迭代器**。例如a是一个非空的vector，则*a.begin()与a[0]的作用相同
 - **所有的容器都可以视作一个“前闭后开[start, end)”的结构**，**end函数返回vector的尾部**，即**第n个元素再往后的“边界”**。***a.end()与a[n]都是越界访问，其中n = a.size()**
 - 下面两份代码都遍历vector\<int>a，并输出它的所有元素

```cpp
#include<vector>
#include<iostream>
using namespace std;

int main()
{
	vector<int> a({1,2,3});
	cout << a[0] << ' ' << *a.begin() << endl;// 结果是1 1，都表示第1个元素1

	// 遍历
	for (int i = 0; i < a.size(); i ++) cout << a[i] << ' ';
	cout << endl;

	// 迭代器遍历
	for (vector<int>::iterator it = a.begin(); it != a.end(); it ++) cout << *it << endl;
    
    // 使用auto遍历
	for (auto it = a.begin(); it != a.end(); it ++) cout << *it << endl;

	// 范围遍历
	for(int x : a) cout << x << ' ' << endl;
	return 0;
}
```
### 1.6 第一元素front/末尾元素back	
 - **front函数返回vector的第一个元素，等价于*a.begin() 和 a[0]**
 - **back函数返回vector的最后一个元素，等价于*a.end() 和 a[a.size() – 1]**
```cpp
#include<vector>
#include<iostream>
using namespace std;

int main()
{
	vector<int> a({1,2,3});
	cout << a.front() << ' ' << a[0] << ' ' << *a.begin() << endl;//都输出1，三个表达式是等价的
	cout << a.back() << ' ' << a[a.size() - 1] << endl;// 均输出3，表达式等价
	return 0;
}
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/e090d09b7dec406ba652ffe4df479ddd.png)
### 1.7 插入末尾push_back/删除末尾pop_back
 - a.push_back(x) **元素x插入到vector a的尾部**
 - b.pop_back() **删除vector a的最后一个元素**
```cpp
#include<vector>
#include<iostream>
using namespace std;

int main()
{
	vector<int> a({1,2,3});
	a.push_back(4);// 往队列最后位置添加元素
	for(int x : a) cout << x << ' ';// 1 2 3 4
	cout << endl;

	a.pop_back();// 去除队列最后位置的元素
	for(int x : a) cout << x << ' ';// 1 2 3
	cout << endl;
}
```
## 2. queue(队列先进先出)
 - **头文件queue**主要包括**循环队列queue**和**优先队列priority_queue**两个容器
![在这里插入图片描述](https://img-blog.csdnimg.cn/554c25893f164bfabe5fad526e5287fa.png)
 - **队列是先进先出的结构，1是先从左边进，也是先从右边出**
 - **队列queue、优先队列priority_queue、栈stack均没有clear()函数，其他都有clear()函数**！！！
### 2.1 声明
```cpp
#include<vector>
#include<queue>
#include<iostream>
using namespace std;

int main()
{
	// 循环队列，也叫队列
	queue<int> q;
	queue<double> q;
	
	struct rec
	{
		int a, x;
	}; 
	queue<rec> q; // 结构体队列
	
	// 优先队列
	priority_queue<int> q;		// 大根堆
	priority_queue<int, vector<int>, greater<int>> q;	     // 小根堆
	priority_queue<pair<int, int>>q;// pair是二元组

	// 大根堆重载小于号
	struct rec
	{
		int a, b;
		bool operator < (const rec& t) const // 重载小于号
		{
			return a < t.a;// 编译器无法比较自定义数据的大小，需要自己定义规则
		}
	}; 
	priority_queue<rec> c; // 定义结构体，内部要重载小于号
	d.push({1,2});

	// 小根堆重载大于号
	struct rec
	{
		int a, b;
		bool operator > (const rec& t) const // 重载大于号
		{
			return a > t.a;// 编译器无法比较自定义数据的大小，需要自己定义规则
		}
	}; 
	priority_queue<rec, vector<rec>, greater<rec>> c; // 定义结构体，内部要重载大于号
	d.push({1,2});
}
```
### 2.2 循环队列 queue(队列结构，无clear函数)
 - push  从队尾插入
 - pop    从队头弹出
 - front  返回队头元素
 - back  返回队尾元素

```cpp
#include<vector>
#include<queue>
#include<iostream>
using namespace std;

int main()
{
	// 循环队列
	queue<int> q;// 队列
	q.push(1); // 队尾插入元素
	q.pop();// 弹出队头元素
	q.front();// 返回队头元素
	q.back();// 返回队尾元素

	q = queue<int>();// 不能用clear函数清空队列，只能用左边的初始化清空
}
```
### 2.3 优先队列 priority_queue(堆结构)
 - push 把元素插入堆
 - pop   删除堆顶元素
 - top    查询堆顶元素（最大值）

```cpp
#include<vector>
#include<queue>
#include<iostream>
using namespace std;

int main()
{
	// 优先队列
	priority_queue<int> a;// 大根堆
	a.push(1); // 插入元素
	a.top();// 返回最大值
	a.pop();// 删除最大值
}
```
## 3. stack(栈先进后出)
 - 头文件stack包含栈，声明和前面的容器类似，结构类似弹夹
 - **push 向栈顶插入**
 - **pop   弹出栈顶元素**
![在这里插入图片描述](https://img-blog.csdnimg.cn/f71afb5a0f434c9ea923c9b4f3b67ec8.png)

```cpp
#include<vector>
#include<queue>
#include<stack>
#include<iostream>
using namespace std;

int main()
{
	stack<int> stk;
	stk.push(1);// 栈顶插入元素
	stk.top();// 返回栈顶元素
	stk.pop();// 弹出栈顶元素
	return 0;
}
```
## 4. deque(双端队列)
 - 双端队列deque是一个支持在两端高效插入或删除元素的连续线性存储空间。它就像是**vector和queue的结合**。与vector相比，deque在头部增删元素仅需要O(1)的时间；与queue相比，deque像数组一样支持随机访问

 - a[] 随机访问元素
 - **begin/end    返回deque的头/尾迭代器**
 - **front/back    队头/队尾元素**
 - **push_back  从队尾入队**
 - **push_front  从队头入队**
 - **pop_back    从队尾出队**
 - **pop_front    从队头出队**
 - **clear            清空队列**

```cpp
#include<vector>
#include<queue>
#include<stack>
#include<deque>
#include<iostream>
using namespace std;

int main()
{
	deque<int> a;
	a.begin(), a.end();
	a.front(), a.back();// 返回队尾和队头元素
	a.push_back(1), a.push_front(2);// 队尾插入1，队头插入2
	a.pop_front(), a.pop_back();// 弹出队尾元素和队头元素
	a.clear();// 清空
	return 0;
}
```
## 5. set(集合)
 - 头文件 set 主要包括 **set 和 multiset 两个容器**，分别是“**有序集合”和“有序多重集合**”，即**前者 set 的元素不能重复**，而**后者可以包含若干个相等的元素**。set 和 multiset 的内部实现是一棵红黑树，它们支持的函数基本相同
### 5.1 声明
```cpp
#include<vector>
#include<queue>
#include<stack>
#include<deque>
#include<iostream>
using namespace std;

int main()
{
	set<int> a;// 元素不能重复
	multiset<double> b;// 元素可以重复

	// set迭代器
	set<int>::iterator it = a.begin();
	it ++;it --;// 表示有序序列的下一个元素/前一个元素
	a.end();// 最后一个元素后一个位置
	
	// 插入元素
	a.insert(x);
	// 查找元素
	a.find(x);// 找到的话返回的是元素的迭代器，没找到则 a.find(x) == a.end()
	if(a.find(x) == a.end()) // 判断x在a中是否存在

	a.lower_bound(x);// 找到大于等于x值的最小元素的迭代器
	a.upper_bound(x);// 找到大于x值的最小元素的迭代器

	a.erase(it);// 删除迭代器
	a.count(x);// 表示x在a里面的个数
	struct rec
	{
		int x, y;
		bool operator < (const rec& t) const // 重载小于号
		{
			return x < t.x;// 编译器无法比较自定义数据的大小，需要自己定义规则
		}
	}; 
	set<rec> c; // 结构体rec中必须定义小于号
	d.push({1,2});
}
```
 - size/empty/clear
 - 与vector类似
### 5.2 迭代器
 - **set 和 multiset 的迭代器称为“双向访问迭代器”，不支持“随机访问”，支持星号(*)解除引用，仅支持”++”和--“两个与算术相关的操作**
 - 设 it 是一个迭代器，例如 set\<int>::iterator it;
 - 若把 it++，则 it 会指向“下一个”元素。这里的“下一个”元素是指在元素从小到大排序的结果中，排在it 下一名的元素。同理，若把 it--，则 it 将会指向排在“上一个”的元素
### 5.3 begin/end
 - 返回集合的首、尾迭代器，时间复杂度均为O(1)
 - **s.begin() 是指向集合中最小元素的迭代器**
 - **s.end() 是指向集合中最大元素的下一个位置的迭代器。换言之，就像 vector 一样，是一个“前闭后开”的形式。因此--s.end()是指向集合中最大元素的迭代器**
### 5.4 insert
 - s.insert(x) 把一个元素x插入到集合 s 中，时间复杂度为O(logn)
 - 在 set 中，若元素已存在，则不会重复插入该元素，对集合的状态无影响
### 5.5 find
 - **s.find(x) 在集合s中查找等于x的元素，并返回指向该元素的迭代器**。若不存在，则返回s.end()。时间复杂度为O(logn)
### 5.6 lower_bound/upper_bound	
 - 这两个函数的用法与find类似，但查找的条件略有不同，时间复杂度为 O(logn)
 - **s.lower_bound(x) 查找大于等于x的元素中最小的一个**，并返回指向该元素的迭代器
 - **s.upper_bound(x) 查找大于x的元素中最小的一个**，并返回指向该元素的迭代器
### 5.7 erase
 - 设it是一个迭代器，s.erase(it) 从s中删除迭代器it指向的元素，时间复杂度为 O(logn)
 - 设x是一个元素，s.erase(x) 从s中删除所有等于x的元素，时间复杂度为 O(k+logn)，其中k是被删除的元素个数
### 5.8 count	
 - **s.count(x) 返回集合s中等于x的元素个数**，时间复杂度为 O(k +logn)，其中k为元素x的个数
## 6. map(红黑树)
 - map 容器是一个键值对 key-value 的映射，其内部实现是一棵以 key 为关键码的红黑树。map的key和value可以是任意类型，其中 key 必须定义小于号运算符
### 6.1 声明
```cpp
#include<vector>
#include<queue>
#include<stack>
#include<deque>
#include<iostream>
#include<map>
using namespace std;

int main()
{
	map<int, int> a;
	a[1] = 2;
	a[1000000] = 3;
	cout << a[1000000] << endl;

	// 数据类型可以自己定义
	map<string, vector<int>> b;
	b["nqq"] = vector<int>({1,2,3,4});
	cout << b["nqq"][2] << endl;// 结果是3
	
	map<key_type, value_type> name;
	map<long, long, bool> vis;
	map<string, int> hash;
	map<pair<int, int>, vector<int>> test;
}
```
 - size/empty/clear/begin/end均与set类似
### 6.2 insert/erase
 - 与set类似，但其参数均是pair<key_type, value_type>
### 6.3 find
 - h.find(x) 在变量名为h的map中查找key为x的二元组
### 6.4 操作符	
 - h[key] 返回key映射的value的引用，时间复杂度为O(logn)
 - 操作符是map最吸引人的地方。我们可以很方便地通过h[key]来得到key对应的value，还可以对h[key]进行赋值操作，改变key对应的value
### 6.5 unorderd_set/unordered_map/bitset
```cpp
#include<vector>
#include<queue>
#include<stack>
#include<deque>
#include<iostream>
#include<map>
#include<unordered_set>
#include<unordered_map>
#include<bitset>
using namespace std;

int main()
{
	unordered_set<int> s;// 哈希表，不能存重复元素
	unordered_multiset<int> s;// 哈希表，能存重复元素

	unordered_map<int, int> c;

	bitset<1000> a;// 中间是数组长度，是0-1串，只有0和1
	a[0] = 1;
	a[1] = 1;
	cout << a.count() << endl;// 表示输出1的个数

	a.set(3);// 可以把第3位设置成1
	a.reset(3);// 把某一位设置成0
	cout << a[3] << endl;// 1
}
```
### 6.6 pair 函数

```cpp
pair<int, string> a;
a = {3, "nqq"};
cout << a.first << ' ' << a.second << endl;
```

# 位运算和常用库函数
## 1. 位运算
 - &：与
 - |： 或
 - ~：非
 - ^： 异或
![在这里插入图片描述](https://img-blog.csdnimg.cn/ce297a81e01b421d928a44f3c02a9038.png)
```cpp
#include<iostream>
using namespace std;

int main()
{
	int a = 3, b = 6;
	cout << (a ^ b) << endl;// 与,加括号
	return 0;
}
```
 - \>>： 右移
 - \<<： 左移
![在这里插入图片描述](https://img-blog.csdnimg.cn/39223ab15f8448109b3cbf4c2dc2a4ea.png)

常用操作：

 - **求 x 的第 k 位数字：x >> k & 1**：向右移动k位，再和1做"与"运算
![在这里插入图片描述](https://img-blog.csdnimg.cn/3a94d520d97b4b35af4c97fc3b2904d9.png)

```cpp
#include<iostream>
using namespace std;

int main()
{
	int a = 13;
	cout << (a >> 2 & 1) << endl;// 看第2为是1还是0
	for(int i = 5;i >= 0; i --) cout << (a >> i & 1) << ' 0';// 输出每一位
}
```
 - **lowbit(x) = x & -x，返回x的最后一位1**
![在这里插入图片描述](https://img-blog.csdnimg.cn/e4aa3581a8dd4aeba46f88fcbd710c8e.png)
 - 推导：-a = a 取反 + 1 

![在这里插入图片描述](https://img-blog.csdnimg.cn/bc7e76b2184240aa8f3d681be09faee4.png)

 - 负a和a取反再加1效果相同
![在这里插入图片描述](https://img-blog.csdnimg.cn/6166c1dd8bff4885bed75c6e4db693dc.png)

```cpp
#include<iostream>
using namespace std;

int main()
{
	int a = 2312321;
	int b = -a;
	int c = ~a + 1;
	
	cout << b << ' ' << c << endl;// -2312321
}
```
## 2. 常用库函数(算法库\<algorithm>)
### 2.1 reverse 翻转
 - 翻转一个vector
```cpp
reverse(a.begin(), a.end());
```
 - 翻转一个数组，元素存放在下标1~n：
```cpp
reverse(a + 1, a + 1 + n);
```
```cpp
#include<iostream>
#include<vector>
#include<algorithm>
using namespace std;

int main()
{
	vector<int> a({1,2,3,4,5});
	reverse(a.begin(),a.end());

	int b[] = {1, 2, 3, 4, 5};
	reverse(b, b + 5);// 右边是返回的是最后一个元素的下一个位置,左闭右开,a[0] —— a[5]

	for(int x : b) cout << x << ' ' ;// 5 4 3 2 1
	cout << endl;
	return 0;
}
```
### 2.2 unique 去重,离散化(重点)
[使用STL中的sort和unique函数进行去重](https://www.acwing.com/solution/content/150444/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/eab9faa61ef74e4885eb3aeab0dc4cef.png)

 - **必须保证相同元素是挨着一起的，才能保证判重**，会把左右不同的元素放在最前面
 - 返回去重之后的尾迭代器（或指针），仍然为**前闭后开**，即这个迭代器是**去重之后末尾元素的下一个位置**。该函数**常用于离散化**，利用**迭代器（或指针）的减法**，可**计算去重后的元素个数**
 - **vector去重**：int m = unique(a.begin(), a.end()) – a.begin()。 unique(a.begin(), a.end())**返回的是所有不同元素的最后一个元素位置的下一位，就是上图的end()位置**
 - **数组去重**，元素存放在下标 1~n(不是0 — n-1)：int m = unique(a + 1, a + 1 + n) – (a + 1)

```cpp
#include<iostream>
#include<vector>
#include<algorithm>
using namespace std;

int main()
{
	// 数组写法
	int a[] = {1, 1, 2, 2, 3, 3, 4};
	int m = unique(a, a + 7) - a;
	cout << m << endl;// 结果是4，表示有4种不同元素
	for(int i = 0; i < m; i ++) cout << a[i] << ' ';// 结果是1,2,3,4
	cout << endl;

	// vector写法,需要用到迭代器
	vector<int> a({1, 1, 2, 2, 3, 3, 4});
	int m = unique(a.begin() - a.end()) - a.begin();
	cout << m << endl;// 结果是4
	for(int i = 0; i < m; i ++) cout << a[i] << ' ';// 结果是1,2,3,4
	cout << endl;

	// 直接删除重复元素
	vector<int> a({1, 1, 2, 2, 3, 3, 4});
	a.erase(unique(a.begin() - a.end()), a.end());
	for(auto x : a) cout << x << ' ';// 1 2 3 4
	cout << endl;
	
	return 0;
}
```
### 2.3 random_shuffle 随机打乱
 - 用法与reverse相同
```cpp
#include<iostream>
#include<vector>
#include<algorithm>
#include<ctime>// 传入时间，当作随机种子
using namespace std;

int main()
{
	vector<int> a({1,2,3,4,5});

	// 加随机种子
	srand(time(0));
	random_shuffle((a.begin(),a.end());// 生成随机数据，每次运行结果都不一样
	for(int x : a) cout << x << ' ';
	cout << endl;

	return 0;
}
```
### 2.4 sort 从小到大排序(重要)
 - 对两个迭代器（或指针）指定的部分进行快速排序。可以在第三个参数传入定义大小比较的函数，或者重载“小于号”运算符
 - 把一个int数组（元素存放在下标1~n）从大到小排序，传入比较函数：
```cpp
int a[MAX_SIZE];
bool cmp(int a, int b) {return a > b; }
sort(a + 1, a + 1 + n, cmp);
```
- 举例1
```cpp
#include<iostream>
#include<vector>
#include<algorithm>
#include<ctime>// 传入时间，当作随机种子
using namespace std;

bool cmp(int a, int b)
{
	return a > b;// 按照从大到小排列，a是否应该排在b前面
}

int main()
{
	vector<int> a({1,2,3,4,5});

	// 从小到大排列
	sort(a.begin(), a.end());
	for(int x : a) cout << x << ' ';// 结果是 1 2 3 4 5
	cout << endl;

	// 从大到小排列
	sort(a.begin(),a.end(),greater<int>)

	// 自定义大小关系
	sort(a.begin(), a.end(), cmp);
	for(int x : a) cout << x << ' ';// 结果是 5 4 3 2 1
	cout << endl;

	return 0;
}
```
 - 把自定义的结构体vector排序，重载“小于号”运算符：
```cpp
struct rec{ int id, x, y; }
vector<rec> a;
bool operator <(const rec &a, const rec &b) {
		return a.x < b.x || a.x == b.x && a.y < b.y;
}
sort(a.begin(), a.end());
```
- 举例2

```cpp
#include<iostream>
#include<vector>
#include<algorithm>
#include<ctime>// 传入时间，当作随机种子
using namespace std;

bool cmp(Rec a, Rec b)// a是否应该排在b前面
{
	return a.x < b.x;// 从小到大的顺序
}

int main()
{
	struct Rec
	{
		int x, y;
	}a[5];

	for(int i = 0; i < 5; i++)
	{
		a[i].x = -i;
		a[i].y = i;
	}

	for(int i = 0;i < n; i++) printf("(%d,%d)",a[i].x,a[i].y);
	cout << endl;

	sort(a, a+5, cmp);// 数组形式

	for(int i = 0;i < n; i++) printf("(%d,%d)",a[i].x,a[i].y);
	cout << endl;
	return 0;
}
```
 - 在自定义结构体里面可以重载小于号

```cpp
#include<iostream>
#include<vector>
#include<algorithm>
#include<ctime>// 传入时间，当作随机种子
using namespace std;

// 排序方法1:使用bool函数
bool cmp(Rec a, Rec b)// a是否应该排在b前面
{
	return a.x < b.x;// 从小到大的顺序
}

int main()
{
	// 排序方法2:使用结构体
	struct Rec
	{
		int x, y;
		bool operator< (const Rec &t) const
		{
			return x < t.x;// x是否能排在t的前面，x小于t.x就排在前面
		}
	}a[5];

	for(int i = 0; i < 5; i++)
	{
		a[i].x = -i;
		a[i].y = i;
	}

	for(int i = 0;i < n; i++) printf("(%d,%d)",a[i].x,a[i].y);
	cout << endl;
	
	// 方法1:函数方法
	sort(a, a + 5, cmp);// 数组形式

	// 方法2:结构体方法
	sort(a, a + 5);

	for(int i = 0;i < n; i++) printf("(%d,%d)",a[i].x,a[i].y);
	cout << endl;
	return 0;
}
```
### 2.5 lower_bound/upper_bound  二分
 - lower_bound 第三个参数传入一个元素x，在两个迭代器（指针）指定的部分上执行**二分查找**，**返回指向第一个大于等于x的元素的位置的迭代器（指针）**
 - upper_bound 用法和 lower_bound 大致相同，唯一的区别是**查找第一个大于x的元素**。当然，两个迭代器（指针）指定的部分应该是提前排好序的
 - 在有序int数组（元素存放在下标1~n）中查找大于等于x的最小整数的下标：
```cpp
int i = lower_bound(a + 1, a + 1 + n,. x) – a;
```
 - 在有序vector<int> 中查找小于等于x的最大整数（假设一定存在）：
```cpp
int y = *--upper_bound(a.begin(), a.end(), x);
```
- 数组形式的用法

```cpp
#include<iostream>
#include<vector>
#include<algorithm>
#include<ctime>// 传入时间，当作随机种子
using namespace std;

int main()
{
	int a[] = {1,2,4,5,6};
	// 返回的是迭代器，数组里就是返回指针
	int *p = lower_bound(a, a + 5, 3);// 大于等于3的第一个元素是4，所以结果是4
	cout << *p << endl;// 结果是4 
	
	int t = lower_bound(a, a + 5, 7) - a;// 可以得到下标, 后面一定要-a
	cout << t << endl;// 结果是5，因为大于等于7的元素没有，指针指向空，就是下标为5的空格

	int t = lower_bound(a, a + 5, 4) - a;
	cout << t << endl;// 结果是2，表示下标为2
	cout << a[t] << endl;// 结果是4，a[2] = 4

	int t = upper_bound(a, a + 5, 4) - a;// 寻找严格大于4的第一个数是5
	cout << t << endl;// 结果是3，表示下标为3
	cout << a[t] << endl;// 结果是4，a[3] = 5
}
```
- vector 用法

```cpp
#include<iostream>
#include<vector>
#include<algorithm>
using namespace std;

int main()
{
	vector<int> a({1,2,4,5,6});
	int t = lower_bound(a.begin(),a.end(),3) - a.begin();
	cout << a[t] << endl;// 结果是4，t = 2
}
```