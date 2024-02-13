# 1 CentOS密码

root密码9702；

mysql密码123；

nqq密码456；

test1密码789

centos7密码：9702

用户：root

查看ip地址：ip addr   

# 2 vs-config配置

```
Host 192.168.78.131
	HostName 192.168.78.131
    User test1
```

如果出现粗光标，按右上NumLK键和右键0(同时)

## vs配置与安装

test1输入cd /，然后输入ll，进入ppp目录，ppp目录下面有很多文件。

test1输入ls，出现app和tools两个文件

# 3 常见问题

### 问题1

字符缺省的是utf8，使用客服端操纵服务器。pwd是根目录
如果无法登陆可以查看centos7的ip地址是不是修改了

192.168.78.128虚拟机ip地址，远程登录centos7

ssh-keygen -t rsa -b 4096生成的密钥存放在c:\user\牛旗旗\.sshroot 

### 问题2

![Linux问题2](E:\BaiduSyncdisk\C++学习\B站C++学习\3.C++项目\Linux基础笔记图片\Linux问题2.png)

解决方法：在test1里面使用ls -a 找到.demo.cpp.swp然后用rm .demo.cpp.swp删除文件即可

# 4 常见操作指令

- **yum -y install tree** 安装树，方便查看程序文件结构
- **yum -y install gdb** 安装gdb

- **yum install psmisc** 安装killall等命令

- **:q按回车键可以开启新的命令行**
- **:x是保存存盘**
- **:w每次写完程序必须用w保存下，修改代码保存**!!!
- man signal 查看signal函数的头文件
- **按a进入insert模式**
- **按esc进入命令模式**

-  vi 打开文件
- **rm删除文件，rm -rf 删除目录**
- cd切换文件
- cd /表示切换到根目录
- cd~表示切换到当前所在目录，比如root ~表示root目录，root/表示根目录。
- groupadd dba创建dba组
- mkdir创建目录名mkdir ccc/ddd表示在ccc目录下创建ddd子目录
- 修改权限——chown -R nqq:dba /aa：将root下面的aa目录转移给nqq用户，dba是组名， aa是目录名，此操作需要在root里面操作，-R表示aa下面的子目录和aa都改变了权限
- mkdir aaa创建目录aaa
- touch 文件名
- cat bbb.cpp 可以打开cpp文件
- ll显示的文件信息更加全面，相当于ls -l
- nqq都是用户，root和dba都是组
- g++ -o bbb bbb.cpp 编译程序，前面的bbb是编译的名称，后面是源文件
- ./bbb运行程序
- linux里面，目录等同于文件夹，使用mkdir创建目录，使用touch创建文件
- **返回上一个级别目录cd ..**

# 5 Linux的hello world

## 5.1 安装C和C++的编译器

yum -y install gcc*

## 5.2 升级编译器

升级软件包：

yum -y install centos-release-scl devtoolset-8-gcc*

启用软件包：

echo "source /opt/rh/devtoolset-8/enable" >>/etc/profile

*#* \*每次启动shell的时候，会执行/etc/profile脚本*

或

mv /usr/bin/gcc /usr/bin/gcc-4.8.5

ln -s /opt/rh/devtoolset-8/root/bin/gcc /usr/bin/gcc

mv /usr/bin/g++ /usr/bin/g++-4.8.5

ln -s /opt/rh/devtoolset-8/root/bin/g++ /usr/bin/g++

## 5.3 安装库函数的帮助文档

yum -y install man-pages

帮助文档的使用

man 级别 命令或函数

显示帮助的界面可以用vi的命令，q退出。使用man strcpy查看帮助文档

**man****的级别：**

**1-****用户命令**；2-系统接口；**3-****库函数**；4-特殊文件，比如设备文件；5-文件；

6-游戏；7-系统的软件包；8-系统管理命令；9-内核。

## 三、编译

gcc/g++ 选项 源代码文件1 源代码文件2 源代码文件n，gcc编译c语言，g++编译c++

 

使用vi编写程序。vi demo.cpp，使用:x存盘退出，使用g++ -o demo demo.cpp语句进行编译，-o表示输出指定的文件名，用demo(与代码名同名生成可编译文件)，demo.cpp是源代码的文件名。会产生demo文件这是编译输出的结果文件。

 

使用./demo输出。如果使用g++ demo.cpp 则生成的文件是a.out。

每次修改完代码后必须用:w进行代码保存！！！！否则之前的错误会一直存在。

 

多文件编写的话，需要不断克隆会话，然后比如设置demo.cpp,public.cpp,public.h等不同文件，使用g++ -o demo demo.cpp public.cpp进行编译。

多文件编写示例：

public.h文件

\#include<iostream>

void func();

 

public.cpp文件

\#include"public.h"

using namespace std;

void func()

{

 cout << "调用func()函数\n";

}

 

demo.cpp文件

\#include<iostream>

\#include"public.h"

using namespace std;

int main()

{

 cout << "hello world!\n";

 func();

}

g++ -o demo demo.cpp public.cpp -O(大写的O不是零0)进行优化，使用ll可以查看。

g++ -o demo demo.cpp public.cpp -O2(O3)

常用选项：

-o     指定输出的文件名，这个名称不能和源文件同名。如果不给出这个选项，则生成可执行文件a.out。

-g     如果想对源代码进行调试，必须加入这个选项。

-On   在编译、链接过程中进行优化处理，生成的[可执行程序](https://baike.baidu.com/item/可执行文件?fromModule=lemma_inlink)效率将更高。

-c     只[编译](https://baike.baidu.com/item/编译?fromModule=lemma_inlink)，不链接成为[可执行文件](https://baike.baidu.com/item/可执行文件?fromModule=lemma_inlink)，通常用于把源文件编译成静态库或动态库。

-std=c++11 支持C++11标准。

优化选项：

-O0： 不做任何优化，这是默认的编译选项。 

-O或-O1： 对程序做部分编译优化，对于大函数，优化编译占用稍微多的时间和相当大的内存。使用本项优化，编译器会尝试减小生成代码的尺寸，以及缩短执行时间，但并不执行需要占用大量编译时间的优化。 

-O2： **这是****推荐的优化等级**。与O1比较而言，O2优化增加了编译时间的基础上，提高了生成代码的执行效率。

-O3： 这是最高最危险的优化等级。用这个选项会延长编译代码的时间，并且在使用gcc4.x的系统里不应全局启用。自从3.x版本以来gcc的行为已经有了极大地改变。在3.x，-O3生成的代码也只是比-O2快一点点而已，而gcc4.x中还未必更快。用-O3来编译所有的软件包将产生更大体积更耗[内存](https://so.csdn.net/so/search?q=内存&spm=1001.2101.3001.7020)的二进制文件，大大增加编译失败的机会或不可预知的程序行为（包括错误）。这样做将得不偿失，记住过犹不及。在gcc 4.x.中使用-O3是不推荐的。

如果使用了优化选项：1）编译的时间将更长；2）目标程序不可调试；3）有效果，但是不可能显著提升程序的性能。

# 6 静态库和动态库

在test1中创建两个文件夹app和tools

## 6.1 程序

### 1. /home/test1/tools/public.h(函数与类的申明)

```
#include <iostream>// 通用函数和类的头文件

// 声明一个通用的函数。
void func();

// 声明一个通用的类。
class AA
{
public:
  void show();
};
```

### 2. /home/test1/tools/public.cpp(函数与类的编写)

```
#include "public.h"
using namespace std;
// 通用函数和类的代码实现文件

// 通用函数的代码实现。
void func()
{
  cout << "调用了func()函数。\n";
}

// 通用类的代码实现。
void AA::show()
{
  cout << "我是一只傻傻鸟。\n";
}
```

### 3. /home/test1/app/demo01.cpp(主函数的编写)重点

- **编译demo1.cpp需要使用全路径 ：g++ -o demo01 demo01.cpp /home/test1/tools/public.cpp**

```
#include "/home/test1/tools/public.h"  // 包含通用函数和
类的头文件。
using namespace std;

int main()
{
  func();    // 调用通用的函数

  AA a;      // 用通用类声明对象
  a.show();  // 调用对象的方法
}
```

## 6.2 静态库

- **生成静态库**：**g++ -c -o lib库名.a 源代码文件清单**
- **生成静态库**：cd tools并且ll之后，再写下面的代码**g++ -c -o libpublic.a public.cpp**，解释如下：-表示只编译不运行，-o指定静态库的文件名，**静态库的命名规则是lib是前缀**，public是库名，.a表示静态库，public.cpp表示源代码的文件名。结果是**生成二进制文件静态库libpublic.a**。
- **静态库规范使用**(编译)：cd app并且ll之后，再写下面的代码**g++ -o demo01 demo01.cpp -L/home/test1/tools -lpublic**   解释如下：-L指定静态库所在目录，-l指向需要链接的库名，不加lib的前缀和.a的后缀。然后需要运行程序**./demo01**

## 6.3 动态库

- **生成动态库**：**g++ -fPIC -shared -o lib库名.so 源代码文件清单**
- **生成动态库**：cd tools并且ll之后，再写如下代码**g++ -fPIC -shared -o libpublic.so public.cpp**，**-fPIC -shared表示制作动态库**，-o后面是动态库文件名。结果是生成动态库文件libpublic.so
- **动态库规范使用**(编译)：cd app并且ll之后，再写下面的代码**g++ -o demo01 demo01.cpp -L/home/test1/tools -lpublic**   解释如下：**-L指定动态库所在目录**，-l指向需要链接的库名，不加lib的前缀和.so的后缀(原来是libpublic.so)。然后需要运行程序**./demo01**
- **运行可执行程序的时候，需要提前设置LD_LIBRARY_PATH环境变量**。程序如下：
- **echo $LD_LIBRARY_PATH**；查看环境变量
- **export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/test1/tools**添加设置环境变量tools
- 重新运行./demo01就可以了

> 如果修改public.cpp重点程序，只需要重新生成动态库**g++ -fPIC -shared -o libpublic.so public.cpp**，不需要重新编译(规范使用动态库)，然后**./demo01**就可以运行
>

> 如果有静态库和动态库，优先使用动态库

# 7 makefile文件编写(难点)

在/home/test1/tools创建一个脚本aa.sh，将静动态库的生成放在里面。

> g++ -c -o libpublic.a public.cpp
>
> g++ -fPIC -shared -o libpublic.so public.cpp

生成的脚本文件没有可执行权限，然后输入命令**sh aa.sh**进行执行(不适合)

## 7.1 app文件

### 1. /home/test1/app/demo01.cpp(主函数的编写)

- **g++ -o demo01 demo01.cpp -L/home/test1/tools -lpublic -L/home/test1/api -lmyapi**： 使用动态库编译，因为这里有两个文件，这里-l是小写的l
- **echo $LD_LIBRARY_PATH**；查看环境变量
- **export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/test1/api**添加设置环境变量api
- ./demo01运行

```
#include "/home/test1/tools/public.h"  // 包含通用函数和
类的头文件
#include "/home/test1/api/myapi.h"  // 包含通用函数和类的头文件
using namespace std;

int main()
{
  func();    // 调用通用的函数。

  AA a;      // 用通用类声明对象。
  a.show();  // 调用对象的方法。
}
```

修改头文件路径，原来是#include "/home/test1/tools/public.h"，现在变成#include "public.h"只保留文件名，不保留路径

```
#include "public.h"  // 包含通用函数和
类的头文件
#include "myapi.h"  // 包含通用函数和类的头文件
using namespace std;

int main()
{
  func();    // 调用通用的函数。

  AA a;      // 用通用类声明对象。
  a.show();  // 调用对象的方法。
}
```

- g**++ -o demo01 demo01.cpp -L/home/test1/tools -lpublic -L/home/test1/api -lmyapi -I/home/test1/tools -I/home/test1/api**，需要在编译demo01时指定路径，-I/home，这里是**大写的I(ai)不是小写的l**

### 2. /home/test1/app/makefile(makefile的编写)—重点

```
all:demo01

demo01:demo01.cpp  // 包括库文件和头文件目录
	g++ -o demo01 demo01.cpp -L/home/test1/tools -lpublic -L/home/test1/api -lmyapi -I/home/test1/tools -I/home/test1/api
	
clean:
	rm -f -demo01
```

有了makefile文件后，可以直接使用**make**语句进行编译，再使用**./demo01**进行运行

make clean会清除一些文件。

> make clean 
>
> make
>
> ./demo01

加入要编译的文件很多，需要写成如下所示的，demo02和demo03均复制成demo01

cp demo01.cpp demo02.cpp
cp demo01.cpp demo03.cpp

```
INCLUDEDIR=-I/home/test1/tools -I/home/test1/api 头文件目录
LIBDIR=-L/home/test1/tools -L/home/test1/api 库文件目录

all:demo01 demo02 demo03

demo01:demo01.cpp
        g++ -o demo01 demo01.cpp $(INCLUDEDIR) $(LIBDIR) -lpublic -lmyapi
        cp demo01 /tmp/.  这句话可以不要，这句话是说把demo01复制到tmp目录

demo02:demo02.cpp
        g++ -o demo02 demo02.cpp $(INCLUDEDIR) $(LIBDIR) -lpublic -lmyapi

demo03:demo03.cpp
        g++ -o demo03 demo03.cpp $(INCLUDEDIR) $(LIBDIR) -lpublic -lmyapi

clean:
        rm -f -demo01 -demo02 -demo03
```

注意事项：

- makefile内容改变后，之前make出来的demoxx文件必须删除，否则会影响到新生成的make文件，报错说覆盖之前的demoxx。

## 7.2 tools文件

### 1. /home/test1/tools/public.h(函数与类的申明)

```
#include <iostream>// 通用函数和类的头文件

// 声明一个通用的函数。
void func();

// 声明一个通用的类。
class AA
{
public:
  void show();
};
```

### 2. /home/test1/tools/public.cpp(函数与类的编写)

```
#include "public.h"
using namespace std;
// 通用函数和类的代码实现文件

// 通用函数的代码实现。
void func()
{
  cout << "调用了func()函数。\n";
}

// 通用类的代码实现。
void AA::show()
{
  cout << "我是一只傻傻鸟。\n";
}
```

### 3. /home/test1/tools/makefile(makefile的编写)—重点

```
# 指定编译的目标文件是libpublic.a和libpublic.so
all:libpublic.a libpublic.so

# 编译libpublic.a需要依赖public.h和public.cpp
# 如果被依赖文件内容发生了变化，将重新编译libpublic.a，g++前面的空格是tab键，这里需要重新退格后用tab键
libpublic.a:public.h public.cpp
        g++ -c -o libpublic.a public.cpp

libpublic.so:public.h public.cpp
        g++ -fPIC -shared -o libpublic.so public.cpp

# clean用于清理编译目标文件，仅在make clean才会执行。
clean:
        rm -f libpublic.a libpublic.so
```

cd tools; ll ;

make clean(清理已经生成的库文件);ll；

直接执行make就可以重新生成静动态库，只要被依赖的文件被改变(任何改变都行)，make就会重新编译

### 7.3 api文件

### 1. /home/test1/api/myapi.h(函数与类的申明)

```
// 另一个通用函数和类的头文件。
#include <iostream>

// 声明一个通用的函数。
void func1();

// 声明一个通用的类。
class BB
{
public:
  void show();
};
```

### 2. /home/test1/api/myapi.cpp(函数与类的编写)

```
// 另一个通用函数和类的代码实现文件。
#include "myapi.h"
using namespace std;

// 通用函数的代码实现。
void func1()
{
  cout << "调用了func1()函数。\n";
}

// 通用类的代码实现。
void BB::show()
{
  cout << "你是一只傻傻鸟。\n";
}
```

### 3. /home/test1/api/makefile(makefile的编写)

```
# 指定编译的目标文件是libmyapi.a和libmyapi.so
all:libmyapi.a libmyapi.so

# 编译libmyapi.a需要依赖myapi.h和myapi.cpp
# 如果被依赖文件内容发生了变化，将重新编译libmyapi.a
libmyapi.a:myapi.h myapi.cpp
        g++ -c -o libmyapi.a myapi.cpp

libmyapi.so:myapi.h myapi.cpp
        g++ -fPIC -shared -o libmyapi.so myapi.cpp

# clean用于清理编译目标文件，仅在make clean才会执行。
clean:
        rm -f libmyapi.a libmyapi.so
```

# 8. main函数参数

## 8.1 mian函数的参数

在程序中，如果不关心main()函数的参数，可以省略不写

main函数有三个参数，argc、argv和envp，它的标准写法如下：

```
int main(int argc,char *argv[],char *envp[])

{
  return 0;
}
```

- **argc：存放程序参数的个数，包括程序本身**
- **argv：字符串的数组，存放了每个参数的值，包括程序本身**
- **envp：字符串的数组，存放了环境变量，数组的最后一个元素是空。应用场景不多**

## 8.2 操作环境变量

### 8.2.1 设置环境变量

```
int setenv(const char *name, const char *value, int overwrite);
```

- name     环境变量名
- value     环境变量的值

overwrite  0-如果环境不存在，增加新的环境变量，如果环境变量已存在，不替换其值；非0-如果环境不存在，增加新的环境变量，如果环境变量已存在，替换其值。

返回值：0-成功；-1-失败（失败的情况极少见）。

注意：此函数设置的环境变量只对本进程有效，不会影响shell的[环境变量](https://baike.baidu.com/item/环境变量?fromModule=lemma_inlink)。如果在运行程序时执行了setenv()函数，进程终止后再次运行该程序，上次的设置是无效的。

### 8.2.2 获取环境变量值

```
char *getenv(const char *name);
```

## 8.3 示例(编译运行)

程序1

```
#include <iostream>
using namespace std;

int main(int argc,char *argv[],char *envp[])
{
  if (argc!=4)
  {
    cout << "表白神器程序的使用方法：./demo 追求者姓名 被追求者姓名 表白内容\n";
    return -1;
  }

  cout << argv[1] << "开始向" << argv[2] << "表白\n";
  cout << argv[3] << endl;
  cout << argv[1] << "表白完成\n";

  return 0;

  cout << "一共有" << argc << "个参数\n";

  // 显示全部的参数
  for (int ii=0;ii<argc;ii++)
  {
    cout << "第" << ii << "个参数：" << argv[ii] << endl;
  }
  // 显示全部的环境变量
  for (int ii=0;envp[ii]!=0;ii++)  // 环境变量数组最后一个元素是0
  {
    cout << envp[ii] << endl;
  }

  // 设置环境变量AA
  setenv("AA","aaaa",0);

  // 显示环境变量AA的值
  cout << "AA=" << getenv("AA") << endl;

  return 0;
}
```

程序2

编译：**g++ -o demo demo.cpp**

运行：./demo

```
#include <iostream>
using namespace std;

int main(int argc,char *argv[],char *envp[])
{
  cout << "一共有" << argc << "个参数\n";

  // 显示全部的参数
  for (int ii=0;ii<argc;ii++)
  {
    cout << "第" << ii << "个参数：" << argv[ii] << endl;
  }
  // 显示全部的环境变量
  for (int ii=0;envp[ii]!=0;ii++)  // 环境变量数组最后一个元素是0
  {
    cout << envp[ii] << endl;
  }

  // 设置环境变量AA
  setenv("AA","aaaa",0);

  // 显示环境变量AA的值
  cout << "AA=" << getenv("AA") << endl;

  return 0;
}
```

# 9. gdb学习

## 9.1 gdb常用命令示例(demobiaobai.cpp)

- 编译：**g++ -o demobiaobai demobiaobai.cpp -g**(这里后面一定要加-g)
- 运行：**./demobiaobai** 张三 西施 我是一只傻傻鸟
- 调试：**gdb demobiaobai**

调试流程

- 设置参数：set args 张三 西施 我是一只傻傻鸟
- 打断点：b 24 在第24行打断点
- 运行程序：run 
- n ：表示执行当前语句，不进入函数内部。
- p ii ：当前ii的值
- set var ii = 8：手工改变ii的值，效果和p ii = 8相同
- c：continue

> 查看行号：需要insert模式下，再将光标定位在需要查看的行，按**ctrl + g**下面可以显示所在行号。可以使用set number显示行号，set nonumber不显示行号。

```
#include <iostream>
using namespace std;

void show(const char *name1,const char *name2,const char *message)
{
  cout << name1 << "开始表白。\n";
  cout << name2 << "：" << message << endl;
}

int main(int argc,char *argv[],char *envp[])
{
  if (argc!=4)
  {
    cout << "表白神器程序的使用方法：./demo 追求者姓名 被追求者姓名 表白内容\n"; return -1;
  }
  cout << "表白前的准备工作一。\n";
  cout << "表白前的准备工作二。\n";
  cout << "表白前的准备工作三。\n";
  cout << "表白前的准备工作四。\n";
  cout << "表白前的准备工作五。\n";

  show(argv[1],argv[2],argv[3]);

  cout << "表白完成。\n";

  for (int ii=0;ii<10;ii++)
  {
    string str="这是第"+to_string(ii)+"个超级女生。";// 这里的to_string函数表示将整型变量变成字符串
    cout << str << endl;
  }

  return 0;
}
```

| **命令** | **简写** |                         **命令说明**                         |
| :------- | :----------: | :----------------------------------------------------------- |
| set args |          | 设置程序运行的参数。  例如：./demo 张三 西施 我是一只傻傻鸟  设置参数的方法是：  set args 张三 西施 我是一只傻傻鸟 |
| break    | b        | 设置断点，b 20 表示在第20行设置断点，可以设置多个断点。删除断点delete  breakpoint 2，2表示断点的序号 |
| run      | r        | 开始运行程序, 程序运行到断点的位置会停下来，如果没有遇到断点，程序一直运行下去。 |
| next     | n        | 执行当前行语句，如果该语句为函数调用，不会进入函数内部。 VS的F10 |
| step     | s        | 执行当前行语句，如果该语句为函数调用，进入函数内部。VS的F11  注意了，如果函数是库函数或第三方提供的函数，用s也是进不去的，因为没有源代码，如果是自定义的函数，只要有源码就可以进去。 |
| print    | p        | 显示变量或表达式的值，如果p后面是表达式，会执行这个表达式。  |
| continue | c        | 继续运行程序，遇到下一个断点停止，如果没有遇到断点，程序将一直运行。  VS的F5 |
| set var  |          | 设置变量的值。  假设程序中定义了两个变量：  int ii;   char name[21];  set var ii=10 把ii的值设置为10；  set var name="西施"。 |
| quit     | q        |                          退出gdb。                           |

## 9.2 gdb调试core文件(demotiaoshi.cpp/test1)

- **编译：g++ -o demotiaoshi demotiaoshi.cpp -g**

- **运行：./demotiaoshi**

Linux缺省不会生成core文件，需要修改系统参数。

调试core文件的步骤如下：

1. 用**ulimit -a**查看当前用户的资源限制参数。左边表示系统资源，右边表示限制的最大值。core file size、open file、stack size这三个参数。stack size 表示栈中分配内存，不能大于8M，open file表示允许打开的文件最大数量，core file size表示core文件的大小，缺省值为0，表示不生成core文件
2. 用**ulimit -c unlimited**把core file size改为unlimited。
3. 运行程序**./demotiaoshi**，产生core文件。用ls进行查看。
4. 运行gdb 程序名 core文件名。**gdb demotiaoshi core.95082**
5. 在gdb中，用**bt**查看函数调用栈。在*ptr = 3的情况下，main函数中调用aa，aa调用bb，在bb里面挂掉的。

```
#include <cstring>
#include <iostream>
using namespace std;

void bb(const int bh,const string xm)
{
  char *ptr=nullptr;
  *ptr=3;// 对空指针进行解引用会发生内存泄漏
  //strcpy(ptr,xm.c_str());// 将空指针作为strcpy函数的第1个参数会发生内存泄漏
}

void aa(const int no,const string name)
{
  bb(3,"冰冰");
}

int main()
{
  aa(8,"西施");

  return 0;
}
```

## 9.3 gdb调试正在运行的程序(demochengxu.cpp)

- gdb 程序名 -p 进程编号
- 编译：**g++ -o demochengxu demochengxu.cpp -g**
- 运行：**./demochengxu**
- 如果要调试运行的程序，需要得到进程编号：**ps -ef |grep demochengxu**，得到./demochengxu 进程编号95147.
- 再**gdb demochengxu -p 95147**(进程编号)

下面的调试和之前的一样

- bt 查看函数调用栈
- n 查看下一步
- set var ii = 1000000 设置变量ii
- c 程序运行结束

```
示例：
#include <unistd.h>
#include <iostream>
using namespace std;

void bb(const int bh,const string xm)
{
  for (int ii=0;ii<1000000;ii++)
  {
    sleep(1);// 每隔一秒显示ii的值
    cout << "ii=" << ii << endl;
  }
}

void aa(const int no,const string name)
{
  bb(3,"冰冰");
}

int main()
{
  aa(8,"西施");

  return 0;
}
```

# 10. linux时间操作

UNIX操作系统根据计算机产生的年代把1970年1月1日作为UNIX的纪元时间，1970年1月1日是时间的中间点，将从1970年1月1日起经过的秒数用一个整数存放

## 10.1 time_t别名

time_t用于表示**时间类型**，它是一个**long类型的别名**，在**<time.h>**文件中定义，表示从1970年1月1日0时0分0秒到现在的秒数

```
typedef long time_t;
```

## 10.2 time()库函数(demotime.cpp)

- **time()库函数用于获取操作系统的当前时间**
- 包含头文件：**<time.h>**
- 声明：

```
time_t time(time_t *tloc);
```

有两种调用方法：

```
// 将空地址传递给time()函数，并将time()返回值赋给变量now
time_t now = time(0);      
或
// 将变量now的地址作为参数传递给time()函数
time_t now; 
time(&now);  
```

- 编译：**g++ -g -o demotime demotime.cpp**
- 运行：**./demotime**

```
#include<iostream>
#include<time.h>// 时间操作头文件
using namespace std;

int main()
{
 time_t now1 = time(0);// 获取当前时间，存放在now1中
 long   now2;
 time(&now2);          // 获取当前时间，存放在now2中
 
 cout << "now1 = " << now1 << endl;// 显示当前时间，1970>年1月1日到现在的秒数
 cout << "now2 = " << now2 << endl;// 显示当前时间，1970>年1月1日到现在的秒数
 return 0;
}
```

## 10.3 tm结构体

time_t是一个长整数，不符合人类的使用习惯，需要转换成tm结构体，tm结构体在<time.h>中声明，如下：2022-10-01 15:30:25  Oct 1,2022 15:30:25

```
struct tm

{
 int tm_year;  // 年份：其值等于实际年份减去1900

 int tm_mon;  // 月份：取值区间为[0,11]，其中0代表一月，11代表12月

 int tm_mday; // 日期：一个月中的日期，取值区间为[1,31]

 int tm_hour;  // 时：取值区间为[0,23]

 int tm_min;  // 分：取值区间为[0,59]

 int tm_sec;   // 秒：取值区间为[0,59]

 int tm_wday; // 星期：取值区间为[0,6]，其中0代表星期天，6代表星期六

 int tm_yday;  // 从每年的1月1日开始算起的天数：取值区间为[0,365] 

 int tm_isdst;  // 夏令时标识符，该字段意义不大
};
```

## 10.4 localtime()库函数(demolocaltime.cpp)

- **localtime()函数用于把time_t表示的时间转换为tm结构体表示的时间**
- **localtime()函数不是线程安全的，localtime_r()是线程安全的**
- 包含**头文件：<time.h>**

函数声明：

```
struct tm *localtime(const time_t *timep);

struct tm *localtime_r(const time_t *timep, struct tm *result);
```

示例：

编译：g++ -g  -o demolocaltime demolocaltime.cpp

运行：./demolocaltime

```
#include <iostream>
#include <time.h>   // 时间操作的头文件
using namespace std;

int main()
{
 time_t now = time(0);  // 获取当前时间，存放在now中
 cout << "now = " << now << endl; // 显示当前时间，1970年1月1日到现在的秒数

 tm tmnow;// tm结构体
 localtime_r(&now,&tmnow);  // 把整数的时间转换成tm结构体

 // 根据tm结构体拼接成中国人习惯的字符串格式
 string stime = to_string(tmnow.tm_year + 1900) + "-"
			  + to_string(tmnow.tm_mon + 1) + "-"
			  + to_string(tmnow.tm_mday) + " "
			  + to_string(tmnow.tm_hour) + ":"
			  + to_string(tmnow.tm_min) + ":"
			  + to_string(tmnow.tm_sec);

 cout << "stime = " << stime << endl;// 2023-9-30 10:36:1
}
```

## 10.5 mktime()库函数

- **mktime()函数的功能与localtime()函数相反，用于把tm结构体时间转换为time_t时间**
- 包含头文件：**<time.h>**
- 函数声明：

```
time_t mktime(struct tm *tm);
```

- 该函数主要**用于时间的运算**，例如：把2022-03-01 00:00:25加30分钟

思路：

1. 解析字符串格式的时间，转换成tm结构体
2. 用mktime()函数把tm结构体转换成time_t时间
3. 把time_t时间加30*60秒
4. 用localtime_r()函数把time_t时间转换成tm结构体
5. 把tm结构体转换成字符串

## 10.6 gettimeofday()库函数

- 用于获取1970年1月1日到现在的秒和当前秒中已逝去的微秒数，可以**用于程序的计时**
- 包含头文件：**<sys/time.h>**
- 函数声明：

```
int gettimeofday(struct timeval *tv, struct timezone *tz);

struct timeval {
  time_t      tv_sec;   /* 1970-1-1到现在的秒数 */
  suseconds_t tv_usec;  /* 当前秒中，已逝去的微秒数 */
}; 

struct timezone {        /* 在实际开发中，派不上用场 */
  int tz_minuteswest;    /* minutes west of Greenwich */ 
  int tz_dsttime;        /* type of DST correction */
}; 
```

程序示例

```
#include <iostream>
#include <sys/time.h>  // gettimeofday()需要的头文件
using namespace std;

int main()
{
  timeval start,end;

  gettimeofday(&start, 0 ); // 计时开始

  for (int ii=0;ii<1000000000;ii++)
    ;

  gettimeofday(&end, 0 );   // 计时结束

  // 计算消耗的时长
  timeval tv;
  tv.tv_usec=end.tv_usec-start.tv_usec;
  tv.tv_sec=end.tv_sec-start.tv_sec;
  if (tv.tv_usec<0)
  {
    tv.tv_usec=1000000-tv.tv_usec;
    tv.tv_sec--;
  }

  cout << "耗时：" << tv.tv_sec << "秒和" << tv.tv_usec << "微秒\n";
}
```

## 10.7 程序睡眠

- 如果需要把程序挂起一段时间，可以**使用sleep()和usleep()两个库函数**
- 包含头文件：**<unistd.h>**
- 函数声明：

```
unsigned int sleep(unsigned int seconds);

int usleep(useconds_t usec);
```

# 11. linux目录操作

## 11.1 目录操作函数

### 11.1.1 获取当前工作目录

- malloc()分配的内存用free释放，new分配的内存用delete释放

包含头文件：**<unistd.h>**

```
char *getcwd(char *buf, size_t size); 

char *get_current_dir_name(void);
```

示例：

```
#include <iostream>
#include <unistd.h>
using namespace std;

int main()
{
 char path1[256];  // linux系统目录的最大长度是255
 getcwd(path1,256);
 cout << "path1 = " << path1 << endl;

 char *path2 = get_current_dir_name();
 cout << "path2 = " << path2 << endl;

 free(path2);  // 注意释放内存
 // malloc()分配的内存用free释放，new分配的内存用delete释放
}
```

### 11.1.2 切换工作目录

包含头文件：**<unistd.h>**

```
int chdir(const char *path);
```

返回值：0-成功；其它-失败（目录不存在或没有权限）

### 11.1.3 创建目录

包含头文件：**<sys/stat.h>**

```
int mkdir(const char *pathname, mode_t mode);
```

- **pathname**：目录名
- **mode**：访问权限，如0755，不要省略前置的0
- 返回值：0-成功；其它-失败（上级目录不存在或没有权限）。 /tmp/aaa  /tmp/aaa/bbb

### 11.1.4 删除目录

包含头文件： **<unistd.h>**

```
int rmdir(const char *path);
```

- path：目录名
- 返回值：0-成功；其它-失败（目录不存在或没有权限）

## 11.2 获取目录文件列表

文件存放在目录中，在处理文件之前，必须先知道目录中有哪些文件，所以要获取目录中文件的列表

### 11.2.1 包含头文件

```
#include <dirent.h>
```

### 11.2.2 相关库函数

步骤一：用**opendir()函数打开目录**

```
DIR *opendir(const char *pathname);
```

- 成功-返回目录的地址，失败-返回空地址

步骤二：用**readdir()函数循环的读取目录**

```
struct dirent *readdir(DIR *dirp);
```

- 成功-返回struct dirent结构体的地址，失败-返回空地址

步骤三：用**closedir()关闭目录**

```
int closedir(DIR *dirp);
```

### 11.2.3 数据结构(demomulu.cpp)

目录指针：

```
DIR *目录指针变量名;
```

- 每次调用readdir()，函数返回struct dirent的地址，存放了本次读取到的内容

```
struct dirent
{
  long d_ino;          // inode number 索引节点号

  off_t d_off;         // offset to this dirent 在目录文件中的偏移

  unsigned short d_reclen;// length of this d_name 文件名长度

  unsigned char d_type;  // the type of d_name 文件类型

  char d_name [NAME_MAX+1];  // file name文件名，最长255字符
};
```

重点关注结构体的d_name和d_type成员

- d_name-文件名或目录名
- d_type-文件的类型，有多种取值，**最重要的是8和4，8-常规文件（A regular file）；4-子目录（A directory）**，其它的暂时不关心。注意，d_name的数据类型是字符，不可直接显示

示例：

- 编译：g++ -g -o demomulu demomulu.cpp

- 运行：./demomulu /home/test1(后面是路径)
- ls -a 效果和上一行相同，4表示目录，8是普通的文件

```
#include <iostream>
#include <dirent.h>    // 目录操作的头文件
using namespace std;

int main(int argc,char *argv[])
{
    if (argc != 2) { cout << "Using ./demo 目录名\n"; return -1; }

 DIR *dir;  // 定义目录指针

 // 打开目录
 if ( (dir = opendir(argv[1])) == nullptr ) return -1;

 // 用于存放从目录中读取到的内容，结构体指针
 struct dirent *stdinfo = nullptr;

 while (1)
 {
  // 读取一项内容并显示出来，读到东西返回读到内容地址，没有读到返回空地址
  if ((stdinfo = readdir(dir)) == nullptr) break;

  cout << "文件名 = " << stdinfo->d_name << "，文件类型 = " << (int)stdinfo->d_type << endl;
 }

 closedir(dir);  // 关闭目录指针
}
```

# 12. linux系统错误

- 在C++程序中，如果调用了库函数，可以通过函数的返回值判断调用是否成功。其实，还有一个整型的全局变量errno，存放了函数调用过程中产生的错误代码
- 如果调用库函数失败，可以通过**errno的值来查找原因**，这也是调试程序的一个重要方法
- **errno在<errno.h>中声明**
- 配合 **strerror()和perror()两个库函数**，可以查看出错的详细信息

## 12.1 strerror()库函数

- strerror() 在**<string.h>**中声明，用于获取错误代码对应的详细信息

```
char *strerror(int errnum);     // 非线程安全

int strerror_r(int errnum, char *buf, size_t buflen); // 线程安全
```

gcc8.3.1一共有133个错误代码。

示例一：

- 编译：g++ -g -o demo demo.cpp
- 运行：./demo

```
#include <iostream>
#include <cstring>
using namespace std;

int main()
{
 int ii;
 for(ii = 0;ii<150;ii++) // gcc8.3.1一共有133个错误代码
 {
  cout << ii << ":" << strerror(ii) << endl;
 }
}
```

示例二：

- man 3 mkdir：可以查看mkdir需要包含的头文件

```
#include <iostream>
#include <cstring>// strerror()函数需要的头文件
#include <cerrno> // errno全局变量的头文件
#include <sys/stat.h> // mkdir()函数需要的头文件
using namespace std;

int main()
{
 int iret = mkdir("/tmp/aaa",0755);
 cout << "iret = " << iret << endl;
 cout << errno << ":" << strerror(errno) << endl;
}
```

- rm -rf /tmp/aaa：有aaa目录的话先删除目录
- g++ -g -o demo demo.cpp
- ./demo

## 12.2 perror()库函数

perror() 在<stdio.h>中声明，用于在控制台显示最近一次系统错误的详细信息，在实际开发中，服务程序在后台运行，通过控制台显示错误信息意义不大。（对调试程序略有帮助）

```
void perror(const char *s);
```

## 12.3 注意事项

### 12.3.1 调用库函数失败不一定会设置errno

并不是全部的库函数在调用失败时都会设置errno的值，以man手册为准（一般来说，不属于系统调用的函数不会设置errno，属于系统调用的函数才会设置errno）。什么是系统调用？百度“库函数和系统调用的区别”。

### 12.3.2 errno不能作为调用库函数失败的标志

errno的值只有在库函数调用发生错误时才会被设置，当库函数调用成功时，errno的值不会被修改，不会主动的置为 0。

在实际开发中，判断函数执行是否成功还得靠函数的返回值，只有在返回值是失败的情况下，才需要关注errno的值。

示例：

```
#include <iostream>
#include <cstring>  // strerror()函数需要的头文件
#include <cerrno>   // errno全局变量的头文件
#include <sys/stat.h> // mkdir()函数需要的头文件
using namespace std;
int main()
{
 int iret = mkdir("/tmp/aaa/bb/cc/dd",0755);
 if (iret!=0)
 {
  cout << "iret=" << iret << endl;
  cout << errno << ":" << strerror(errno) << endl;
  perror("调用mkdir(/tmp/aaa/bb/cc/dd)失败");
 }
 iret = mkdir("/tmp/dd",0755);
 if (ireet != 0)
 {
  cout << "iret = " << iret << endl;
  cout << errno << ":" << strerror(errno) << endl;
  perror("调用mkdir(/tmp/dd)失败");
 }
}
```

# 13. 目录和文件的更多操作

## 13.1 access()库函数

- access()函数用于判断当前用户对目录或文件的存取权限

包含头文件：

```
#include <unistd.h>
```

函数声明：

```
int access(const char *pathname, int mode);
```

参数说明：

- pathname 目录或文件名
- mode     需要判断的存取权限
- 在头文件<unistd.h>中的预定义如下：已经定义好的宏

```
#define R_OK  4  // 判断是否有读权限
#define W_OK 2  // 判断是否有写权限
#define X_OK  1  // 判断是否有执行权限
#define F_OK  0  // 判断是否存在
```

返回值：

- 当pathname满足mode权限返回0，不满足返回-1，errno被设置
- 在实际开发中，access()函数主要用于判断目录或文件是否存在

> g++ -o demo demo.cpp
>
> ./demo
>
> ls
>
> ./demo demo
>
> ./demo demo.cpp

```
#include <iostream>
#include <cstdio>
#include <sys/stat.h> // mkdir()函数需要的头文件
#include <unistd.h>
using namespace std;

int main(int argc, char *argv[])
{
  if(argc != 2) {cout << "Using:./demo 文件或目录名\n";return -1;}
  if(access(argv[1],F_OK)!=0)
  {
    cout << "文件或目录" << argv[1] << "不存在\n";return -1;
  }
  cout << "文件或目录" << argv[1] << "已存在\n"; 
  return 0;
}
```

## 13.2 stat()库函数

### 13.2.1 stat结构体

s**truct stat结构体用于存放目录或文件的详细信息**，如下：

```
struct stat
{
 dev_t st_dev;    // 文件的设备编号
 ino_t st_ino;     // 文件的i-node
 mode_t st_mode; // 文件的类型和存取的权限
 nlink_t st_nlink;  // 连到该文件的硬连接数目，刚建立的文件值为1
 uid_t st_uid;     // 文件所有者的用户识别码
 gid_t st_gid;     // 文件所有者的组识别码
 dev_t st_rdev;    // 若此文件为设备文件，则为其设备编号
 off_t st_size;     // 文件的大小，以字节计算
 size_t st_blksize;  // I/O 文件系统的I/O 缓冲区大小
 size_t st_blocks;  // 占用文件区块的个数
 time_t st_atime;  // 文件最近一次被存取或被执行的时间，在用mknod、 utime、read、write 与tructate 时改变
 time_t st_mtime;  // 文件最后一次被修改的时间，在用mknod、 utime 和write 时才会改变
 time_t st_ctime;  // 最近一次被更改的时间，在文件所有者、组、 权限被更改时更新
};
```

- struct stat结构体的成员变量比较多，重点关注**st_mode、st_size和st_mtime成员**。注意：**st_mtime是一个整数表示的时间，需要程序员自己写代码转换格式**
- st_mode成员的取值很多，用以下两个宏来判断：

```
S_ISREG(st_mode) // 是否为普通文件，如果是，返回真。 

S_ISDIR(st_mode) // 是否为目录，如果是，返回真。
```

### 13.2.2 stat()库函数

- 包含头文件：

```
#include <sys/stat.h>
```

- 函数声明：

```
int stat(const char *path, struct stat *buf);
```

- **stat()函数获取path参数指定目录或文件的详细信息，保存到buf结构体中**
- 返回值：0-成功，-1-失败，errno被设置

示例：

```
#include <stdio.h>
#include <iostream>
#include <cstdio>
#include <sys/stat.h>
#include <unistd.h>
using namespace std;

int main(int argc,char *argv[])
{
  if (argc != 2) { cout << "Using:./demo 文件或目录名\n"; return -1; }
 struct stat st; // 存放目录或文件详细信息的结构体。
 
 // 获取目录或文件的详细信息
 if (stat(argv[1],&st) != 0)// 调用stat函数将目录或者文件名传递进去，以及结构体地址
 {
  cout << "stat(" << argv[1] << "):" << strerror(errno) << endl; return -1;
 }
 if (S_ISREG(st.st_mode))
 {
    cout << argv[1] << "是一个文件(" << "mtime=" << st.st_mtime << ",size=" << st.st_size << ")\n";
 }
  
 if (S_ISDIR(st.st_mode))
 {
    cout << argv[1] << "是一个目录(" << "mtime=" << st.st_mtime << ",size=" << st.st_size << ")\n";
 }// 时间用整数表示，实际开发中需要转换成字符串
}
```

## 13.3 utime()库函数(需要二次封装)

- utime()函数用于修改目录或文件的时间
- 包含头文件：

```
#include <sys/types.h>
#include <utime.h>
```

- 函数声明：

```
int utime(const char *filename, const struct utimbuf *times);
```

- utime()函数用来**修改参数filename的st_atime和st_mtime**。如果参数times为空地址，则设置为当前时间。

```
time_t st_atime;  // 文件最近一次被存取或被执行的时间，在用mknod、 utime、read、write 与tructate 时改变
 time_t st_mtime;  // 文件最后一次被修改的时间，在用mknod、 utime 和write 时才会改变
```

- 结构utimbuf 声明如下：

```
struct utimbuf
{
 time_t actime;
 time_t modtime;
};
```

- 返回值：0-成功，-1-失败，errno被设置

## 13.4 rename()库函数

- rename()函数用于重命名目录或文件，相当于操作系统的mv命令
- 包含头文件：

```
#include <stdio.h>
```

- 函数声明：

```
int rename(const char *oldpath, const char *newpath);
```

- 参数说明：

```
oldpath   原目录或文件名
newpath  目标目录或文件名
```

- 返回值：0-成功，-1-失败，errno被设置

## 13.5 remove()库函数

- **remove()函数用于删除目录或文件，相当于操作系统的rm命令**
- 包含头文件：

```
#include <stdio.h>
```

- 函数声明：

```
int remove(const char *pathname);
```

- 参数说明：

```
pathname 待删除的目录或文件名
```

- 返回值：0-成功，-1-失败，errno被设置

# 14. Linux的信号

## 14.1 信号的基本概念

- 信号（signal）是软件中断，是进程之间相互传递消息的一种方法，用于通知进程发生了事件，但是，不能给进程传递任何数据
- 信号产生的原因有很多，在**Shell中，可以用kill和killall命令发送信号**：

```
kill -信号的类型 进程编号
killall -信号的类型 进程名
yum install psmisc 安装killall等命令
```

```
#include<iostream>
#include<unistd.h>
using namespace std;

int main(int argc,char *argv[])
{
	while(true)
	{
		cout << "执行了一个任务\n";
		sleep(1);
	}
}
```

> 切换到第2个窗口编译运行程序
>
> g++ -o demo demo.cpp
>
> ./demo
>
> 切换到第3个窗口
>
> killall demo(向进程发送信号，进程停止)
>
> 切换到第3个窗口
>
> killall -15 demo(-指定信号种类)
>
> 切换到第3个窗口
>
> killall -1 demo(-指定信号种类)显示程序挂起
>
> 切换到第3个窗口
>
> killall -8 demo(-指定信号种类)显示浮点数例外
>

## 14.2 信号的类型

|   信号名    | 信号值 | 默认处理动作 |                    发出信号的原因                    |
| :---------: | :----: | :----------: | :--------------------------------------------------: |
|   SIGHUP    |   1    |      A       |               终端挂起或者控制进程终止               |
| **SIGINT**  | **2**  |    **A**     |                  **键盘中断Ctrl+c**                  |
|   SIGQUIT   |   3    |      C       |                  键盘的退出键被按下                  |
|   SIGILL    |   4    |      C       |                       非法指令                       |
|   SIGABRT   |   6    |      C       |               由abort(3)发出的退出指令               |
|   SIGFPE    |   8    |      C       |                       浮点异常                       |
| **SIGKILL** | **9**  |   **AEF**    |        **采用kill  -9 进程编号 强制杀死程序**        |
| **SIGSEGV** | **11** |   **CEF**    | **无效的内存引用（数组越界、操作空指针和野指针等）** |
|   SIGPIPE   |   13   |      A       |          管道破裂，写一个没有读端口的管道。          |
| **SIGALRM** | **14** |    **A**     |           **由闹钟alarm()函数发出的信号**            |
| **SIGTERM** | **15** |    **A**     | **采用“kill  进程编号”或“killall 程序名”通知程序。** |
|   SIGUSR1   |   10   |      A       |                   用户自定义信号1                    |
|   SIGUSR2   |   12   |      A       |                   用户自定义信号2                    |
| **SIGCHLD** | **17** |    **B**     |                  **子进程结束信号**                  |
|   SIGCONT   |   18   |              |              进程继续（曾被停止的进程）              |
|   SIGSTOP   |   19   |     DEF      |                       终止进程                       |
|   SIGTSTP   |   20   |      D       |             控制终端（tty）上按下停止键              |
|   SIGTTIN   |   21   |      D       |               后台进程企图从控制终端读               |
|   SIGTTOU   |   22   |      D       |               后台进程企图从控制终端写               |
|    其它     |  <=64  |      A       |                      自定义信号                      |

处理动作一项中的字母含义如下：

- A 缺省的动作是终止进程
- B 缺省的动作是忽略此信号，将该信号丢弃，不做处理
- C 缺省的动作是终止进程并进行内核映像转储（core dump）
- D 缺省的动作是停止进程，进入停止状态的程序还能重新继续，一般是在调试的过程中
- **E 信号不能被捕获**
- **F 信号不能被忽略**

## 14.3 信号的处理(test1/demo.cpp)

- 进程对信号的处理方法有三种：

1. 对该信号的处理采用系统的默认操作，**大部分的信号的默认操作是终止进程，少部分不会终止进程，比如-17**
2. 设置信号的处理函数，收到信号后，由该函数来处理，比如signal
3. 忽略某个信号，对该信号不做任何处理，就像未发生过一样

- signal()函数可以设置程序对信号的处理方式

函数声明：

```
sighandler_t signal(int signum, sighandler_t handler);
```

- **参数signum表示信号的编号（信号的值）**

- **参数handler表示信号的处理方式**，有三种情况：

1. SIG_DFL：恢复参数signum信号的处理方法为默认行为

```
signal(signum,SIG_DFL);// 恢复信号的处理方法为默认行为
```

2. 一个自定义的处理信号的函数，函数的形参是信号的编号

3. SIG_IGN：忽略参数signum所指的信号

```
#include<iostream>
#include<signal.h>// signal的头文件
#include<unistd.h>
using namespace std;

// 信号处理函数
void func(int signum)
{
   cout << "收到了信号："<< signum << endl;
   signal(signum,SIG_DFL);// 恢复信号的处理方法为默认行为
}

void func1(int sig)
{
	cout << "闹钟响了，执行定时任务\n";
	alarm(5);// 处理函数中这行代码不能少，少了这行代码闹钟只会响一次
}

int main(int argc,char *argv[])
{
	// man signal可以查看函数需要包含的头文件
	// sighandler_t signal(int signum, sighandler_t handler);
	// 除了收到1和15会执行收到信号func函数，其余都是默认操作(大部分是终止进程)
	// 如果接收到1的信号，就执行func
	signal(1,func);// 注册回调函数func(),收到信号后，回调func()函数。回调func()函数时，把信号的编号传给func()函数
	// 如果收到15的信号，也去执行
    signal(15,func);
    signal(2,SIG_IGN);// 忽略2的信号，效果等同于signal(SIGINT,SIG_IGN)
    
    signal(9,func);// 显示程序已杀死，这句代码是无效的，9的信号无法被捕获
    signal(9,SIG_IGN);// 这行代码无效，9的信号不能被忽略
    alarm(5);// 闹钟(定时器)，5秒后将向本程序发送14的信号，闹钟响了程序退出
    // SIGALRM 14 A 由闹钟alarm()函数发出的信号
    signal(14,func1);// 设置定时任务函数
    
	while(true)
	{
		cout << "执行了一个任务\n";
		sleep(1);
	}
}
```

- 设置信号的处理函数，收到信号后，由该函数来处理，比如signal，执行下面操作

> 切换第2个窗口编译运行程序
>
> g++ -o demo demo.cpp
>
> ./demo
>
> 切换第3个窗口
>
> killall -15 demo —— 显示收到信号15
>
> killall -1 demo —— 显示收到信号1
>
> killall -2 dmeo —— 信号终止

- 忽略某个信号，对该信号不做任何处理，就像未发生过一样。在程序里面添加signal(2,SIG_IGN)

> 切换第2个窗口编译运行程序
>
> g++ -o demo demo.cpp
>
> ./demo
>
> 切换第3个窗口
>
> killall -2 dmeo —— 信号被忽略了，没有反应
>
> killall -3 demo —— 退出程序

## 14.4 信号的作用

- 服务程序运行在后台，如果想让中止它，杀掉不是个好办法，因为进程被杀的时候，是突然死亡，没有安排善后工作
- 如果向服务程序发送一个信号，服务程序收到信号后，调用一个函数，在函数中编写善后的代码，程序就可以有计划的退出
- **如果向服务程序发送0的信号，可以检测程序是否存活**

```
#include <iostream>
#include <unistd.h>
#include <signal.h>
using namespace std;

void EXIT(int sig)
{
  cout << "收到了信号：" << sig << endl;
  cout << "正在释放资源，程序将退出......\n";

  // 有很多数据需要释放，比如保存数据，关闭文件，断开与数据库的连接，断开网络连接等
  // 以下是释放资源的代码
  cout << "程序退出\n";
  exit(0);  // 进程退出
}

int main(int argc,char *argv[])
{
  // 忽略全部的信号，防止程序被信号异常中止
  for (int ii=1;ii<=64;ii++) signal(ii,SIG_IGN);

  // 如果收到2和15的信号（Ctrl+c和kill、killall），本程序将主动退出
  signal(2,EXIT);  signal(15,EXIT);

  while (true)
  {
    cout << "执行了一次任务\n";
    sleep(1);
  }
}
```

> 编译：g++ -o demo demo.cpp 
>
> 运行：./demo
>
> 按ctrl + c程序释放资源，体面退出
>
> 运行：./demo
>
> 执行killall demo 效果和上面的ctrl+c相同

> 编译：g++ -o demo demo.cpp 
>
> 运行：./demo
>
> killall -0 demo —— 程序正在运行不会有任何错误

## 14.5 发送信号

- Linux操作系统提供了kill和killall命令向进程发送信号，在程序中，可以用kill()函数向其它进程发送信号
- 函数声明：

```
int kill(pid_t pid, int sig);
```

- kill()函数将参数sig指定的信号给参数pid 指定的进程

- 参数pid 有几种情况：

1. pid>0 将信号传给进程号为pid 的进程
2. pid=0 将信号传给和当前进程相同进程组的所有进程，常用于父进程给子进程发送信号，注意，发送信号者进程也会收到自己发出的信号
3. pid=-1 将信号广播传送给系统内所有的进程，例如系统关机时，会向所有的登录窗口广播关机信息

- sig：准备发送的信号代码，假如其值为0则没有任何信号送出，但是系统会执行错误检查，通常会利用sig值为零来检验某个进程是否仍在运行

- 返回值说明： 成功执行时，返回0；失败返回-1，errno被设置

# 15. 进程终止

- 有8种方式可以中止进程，其中5种为正常终止，它们是：

1. 在main()函数用return返回
2. 在任意函数中调用exit()函数
3. 在任意函数中调用\_exit()或_Exit()函数

```
void func2()
{
  cout << "调用func2()\n";
  // exit(0);// 终止进程
  return;
}

void func1()
{
   cout << "调用func1()\n";
   func2();
   cout << "回到func1()函数\n";
}

int main()
{
  fun1();// main函数调用func1，在func2中调用exit(0)，不回到main函数中直接退出
  cout << "回到main函数\n";
}
```

- func2()最后是exit(0)

> g++ -o demo demo.cpp
>
> ./demo
>
> 显示
>
> 调用func1();
>
> 调用func2();

- func2()最后改为return;

> g++ -o demo demo.cpp
>
> ./demo
>
> 显示
>
> 调用func1();
>
> 调用func2();
>
> 回到func1()函数
>
> 回到main函数

4. 最后一个线程从其启动例程（线程主函数）用return返回

5. 在最后一个线程中调用pthread_exit()返回；

- 异常终止有3种方式，它们是：

6. 调用abort()函数中止
7. 接收到一个信号
8. 最后一个线程对取消请求做出响应

## 15.1 进程终止的状态

- 在main()函数中，return的返回值即终止状态，如果没有return语句或调用exit()，那么该进程的终止状态是0
- 在Shell中，查看进程终止的状态：echo $?

```
void func2()
{
  cout << "调用func2()\n";
  // exit(0);// 终止进程
  return;
}
void func1()
{
   cout << "调用func1()\n";
   func2();
   cout << "回到func1()函数\n";
}
int main()
{
   // return 1;
   // exit(0);
   exit(5);
}
```

> main函数中什么代码均没有
>
> g++ -o demo demo.cpp
>
> ./demo
>
> echo $?
>
> 结果为0
>
> 
>
> main函数中添加 return 1;
>
> g++ -o demo demo.cpp
>
> ./demo
>
> echo $?
>
> 结果为1
>
> 
>
> main函数中添加 exit(0);
>
> g++ -o demo demo.cpp
>
> ./demo
>
> echo $?
>
> 结果为0
>
> 
>
> main函数中添加 exit(5);
>
> g++ -o demo demo.cpp
>
> ./demo
>
> echo $?
>
> 结果为5

- 正常终止进程的3个函数（exit()和_Exit()是由ISO C说明的，_exit()是由POSIX说明的）

```
void exit(int status);
void _exit(int status);
void _Exit(int status);
```

- status也是进程终止的状态
- 如果进程被异常终止，终止状态为非0。  终止状态主要用于：服务程序的调度、日志和监控

## 15.2 资源释放的问题

- retun表示函数返回，会调用局部对象的析构函数，main()函数中的return还会调用全局对象的析构函数
- **exit()表示终止进程，不会调用局部对象的析构函数，只调用全局对象的析构函数**
- exit()会执行清理工作，然后退出，\_exit()和_Exit()直接退出，不会执行任何清理工作

```
#include<iostream>
#include<unisted.h>
using namespace std;

struct AA
{
	string name;// 用于区分不同的对象
	AA(const string & str):name(str){}// 构造函数
	~AA()
	{
		cout << name << "调用析构函数\n";
	}
}
AA a1("对象a1");// 定义全局对象a1

int main(int argc,char *argv[])
{
	AA a2("对象a2");// 定义局部对象a2
	// return 0;
	// exit(0);
	_exit(0);// 不执行清理工作，而是直接退出
}
```

> main函数是return 0;
>
> g++ -o demo demo.cpp
>
> ./demo
>
> 显示
>
> 对象a2调用析构函数
>
> 对象a1调用析构函数
>
> 
>
> main函数是exit(0);
>
> g++ -o demo demo.cpp
>
> ./demo
>
> 显示(未调用局部对象析构函数)
>
> 对象a1调用析构函数
>
> 
>
> main函数是_exit(0);
>
> g++ -o demo demo.cpp
>
> ./demo
>
> 均未调用析构函数

## 15.3 进程的终止函数

- 进程可以用atexit()函数登记终止函数（最多32个），这些函数将由exit()自动调用

```
int atexit(void (*function)(void));
```

- exit()调用终止函数的顺序与登记时相反。 进程退出前的收尾工作

```
#include<iostream>
#include<unisted.h>
using namespace std;

void func1()
{
	cout << "调用func1()\n";
}
void func2()
{
	cout << "调用func2()\n";
}

int main(int argc,char *argv[])
{
	atexit(func1);// 登记第1个进程终止函数
	atexit(func2);// 登记第2个进程终止函数
	//return 0;
	//exit(1);
	_exit(1);
}
```

> main函数最后是return 0;
>
> g++ -o demo demo.cpp
>
> ./demo
>
> 显示
>
> 调用func2()
>
> 调用func1()
>
> 
>
> main函数最后是exit(1);
>
> g++ -o demo demo.cpp
>
> ./demo
>
> 显示
>
> 调用func2()
>
> 调用func1()
>
> 
>
> main函数最后是_exit(1);
>
> g++ -o demo demo.cpp
>
> ./demo
>
> 显示 无

# 16. 调用可执行程序

Linux提供**system()函数和exec函数族**，在C++程序中，可以执行其它的程序（二进制文件、操作系统命令或Shell脚本）

## 16.1 system()函数(demo_system.cpp)

- system()函数提供一种简单的执行程序的方法，把**需要执行的程序和参数用一个字符串传给system()函数就行了**

- 函数的声明：

```
// man system可以得到system头文件
int system(const char * string);
```

- system()函数的返回值比较麻烦

1. 如果执行的程序不存在，system()函数返回非0
2. 如果执行程序成功，并且被执行的程序终止状态是0，system()函数返回0
3. 如果执行程序成功，并且被执行的程序终止状态不是0，system()函数返回非0

```
#include <iostream>
#include <unistd.h>
using namespace std;

int main(int argc,char *argv[])
{
 int ret = system("/bin/ls -l /tmp"); // -l /tmp是参数
 cout << "ret = " << ret << endl;
 perror("system");
 }
```

> 在新窗口中执行：/bin/ls -l /tmp
>
> g++ -o demo_system demo_system.cpp
>
> ./demo_system
>
> 效果和/bin/ls -l /tmp相同

- demo.cpp代码

```
#include <iostream>
#include <unistd.h>
using namespace std;

int main(int argc,char *argv[])
{
 int ret = system("/home/test1/demo01"); 
 cout << "ret = " << ret << endl;
 perror("system");
}
```

- demo01.cpp

```
#include <iostream>
#include <unistd.h>
using namespace std;

int main(int argc,char *argv[])
{
	cout << "运行demo01\n";
	return 0;
}
```

> 切换至第3个窗口
>
> 编译demo01：g++ -o demo01 demo01.cpp
>
> 切换至第4个窗口编译运行demo
>
> 编译demo：g++ -o demo demo.cpp
>
> 运行demo：./demo
>
> 显示
>
> 运行了demo01
>
> ret = 0
>
> system：Success

- 将return 0改成return 5(8)

> 切换至第3个窗口
>
> 编译demo01：g++ -o demo01 demo01.cpp
>
> 切换至第4个窗口编译运行demo
>
> 编译demo：g++ -o demo demo.cpp
>
> 运行demo：./demo
>
> 显示
>
> 运行了demo01
>
> ret = 1280(2048)
>
> system：Success

## 16.2 exec函数族

- exec函数族提供了另一种在进程中调用程序（二进制文件或Shell脚本）的方法
- exec函数族的声明如下：第1和第4个加星的着重学习

```
**int execl(const char \*path, const char \*arg, ...);**
int execlp(const char *file, const char *arg, ...);
int execle(const char *path, const char *arg,...,char * const envp[]);
**int execv(const char \*path, char \*const argv[]);**
int execvp(const char *file, char *const argv[]);
int execvpe(const char *file, char *const argv[],char *const envp[]);
```

注意：

- 如果执行程序失败则直接返回-1，失败原因存于errno中
- **新进程的进程编号与原进程相同，但是新进程取代原进程的代码段、数据段和堆栈**
- 如果执行成功则函数不会返回，当在主程序中成功调用exec后，被调用的程序将取代调用者程序，也就是说，exec函数之后的代码都不会被执行
- 在实际开发中，**最常用的是execl()和execv()**，其它的极少使用。

示例1：

- demo代码

```
#include <iostream>
#include <string.h>
#include <unistd.h>
using namespace std;

int main(int argc,char *argv[])
{
// execl参数第1个参数是需要执行的程序，第2个是需要执行的程序，第3个是需要执行程序的参数，最后是0，不能省略，表示参数已结束
 int ret = execl("/bin/ls","/bin/ls","-lt","/tmp",0);
 cout << "ret = " << ret << endl;// ret显示execl的返回值
 perror("execl");// 显示系统错误

 /*
 char *args[10];
 args[0]="/bin/ls";
 args[1]="-lt";
 args[2]="/tmp";
 args[3]=0;   // 这行代码不能省略。
 int ret=execv("/bin/ls",args);
 cout << "ret=" << ret << endl;
 perror("execv");
 */
}
```

> 在新窗口中执行：/bin/ls -lt /tmp
>
> 切换到新窗口编译：g++ -o demo demo.cpp
>
> 运行./demo
>
> 效果和/bin/ls -lt /tmp相同

示例2：

- 显示进程编号的代码demo01

```
#include <iostream>
#include <string.h>
#include <unistd.h>
using namespace std;

int main(int argc,char *argv[])
{
// 新进程的进程编号与原进程相同，但是新进程取代了原进程的代码段、数据段和堆栈
	// getpid表示获取自己的进程编号
   cout << "demo01 本进程编号是："<< getpid() << endl;
   int ret = execl("/home/test1/demo01","/home/test1/demo01",0);// 最后一个参数0不能省略
   return 0;
}
```

- demo代码

```
#include <iostream>
#include <string.h>
#include <unistd.h>
using namespace std;

int main(int argc,char *argv[])
{
// 新进程的进程编号与原进程相同，但是新进程取代了原进程的代码段、数据段和堆栈
 /* 注释下面代码，这个是参数代码
 int ret = execl("/bin/ls","/bin/ls","-lt","/tmp",0);
 cout << "ret = " << ret << endl;// ret显示execl的返回值
 perror("execl");// 显示系统错误
 */
 
  cout << "demo 本进程编号是："<< getpid() << endl;// 这里是demo
 int ret = execl("/home/test1/demo01","/home/test1/demo01",0);// execl调用demo01

 /*
 char *args[10];
 args[0]="/bin/ls";
 args[1]="-lt";
 args[2]="/tmp";
 args[3]=0;   // 这行代码不能省略。
 int ret=execv("/bin/ls",args);
 cout << "ret=" << ret << endl;
 perror("execv");
 */
}
```

> 切换到新窗口编译：g++ -o demo demo.cpp
>
> 运行./demo
>
> 显示
>
> demo  本进程编号是8826(程序每次运行进程编号是不同的)
>
> demo01 本进程编号是8826
>
> (demo和demo01的进程编号相同)

- 修改demo将excel改成system

```
#include <iostream>
#include <string.h>
#include <unistd.h>
using namespace std;

int main(int argc,char *argv[])
{
	// getpid表示获取自己的进程编号
   cout << "demo 本进程编号是："<< getpid() << endl;
   int ret = system("/home/test1/demo01");// 最后一个参数0不能省略
   return 0;
}
```

> 切换到新窗口编译：g++ -o demo demo.cpp
>
> 运行./demo
>
> 显示
>
> demo  本进程编号是8876
>
> demo01 本进程编号是8877
>
> (demo和demo01的进程编号不同)

- demo中增加两行代码cout和perror

```
#include <iostream>
#include <string.h>
#include <unistd.h>
using namespace std;

int main(int argc,char *argv[])
{
	// getpid表示获取自己的进程编号
   cout << "demo 本进程编号是："<< getpid() << endl;
   int ret = system("/home/test1/demo01");// 最后一个参数0不能省略
   cout << "ret = " << ret << endl;
   perror("system");
   return 0;
}
```

> 切换到新窗口编译：g++ -o demo demo.cpp
>
> 运行./demo
>
> 显示
>
> demo  本进程编号是8905
>
> demo01 本进程编号是8906
>
> ret = 0
>
> system: Success

- demo中重新修改代码,system换成execl

```
#include <iostream>
#include <string.h>
#include <unistd.h>
using namespace std;

int main(int argc,char *argv[])
{
	// getpid表示获取自己的进程编号
   cout << "demo 本进程编号是："<< getpid() << endl;
   int ret = execl("/home/test1/demo01","/home/test1/demo01",0);// 最后一个参数0不能省略
   cout << "ret = " << ret << endl;
   perror("execl");
   return 0;
}
```

> 切换到新窗口编译：g++ -o demo demo.cpp
>
> 运行./demo
>
> 显示
>
> demo  本进程编号是8921
>
> demo01 本进程编号是8921
>
> (编号相同)

system执行完程序后，流程会回来；execl执行进程则新进程取代原进程的数据段代码段，原代码被取代，流程无法回来
