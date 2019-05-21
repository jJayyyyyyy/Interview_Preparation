[博客链接](https://segmentfault.com/a/1190000018346507)

##	Java

*	[JavaNotes](https://github.com/jJayyyyyyy/javanotes)

	<br>

*	[Java 学习笔记](https://segmentfault.com/a/1190000019024444)

	<br>

###	基本知识

*	基本数据类型

	```java
	// 整数
	byte 1
	short 2
	int 4
	long 8

	// 浮点数
	float 4
	double 8

	// 逻辑
	boolean 1

	// 字符
	char 2, Unicode
	```

	<br>

*	Override, 覆盖/重写, 返回值和形参都不能改变

	<br>

*	Overload, 重载

	<br>

###	栈和堆

*	基本数据类型的变量, 在栈里面, 复制变量的时候, 复制的是值

	引用类型的变量, 在堆, 变量只是引用, 类似于指针, 只能指向特定对象, 不能乱指, 复制变量的时候, 复制的是引用

	引用类型: 数组, 类, 接口

	<br>

###	抽象和接口

*	抽象类跟接口的区别

	[JavaNotes](https://github.com/jJayyyyyyy/JavaNotes/blob/master/note12.md)

	[抽象类和接口的区别](https://www.jianshu.com/p/038f0b356e9a)

	抽象类, 是声明, 抽象类不能instantiate(实例化), 也就是不能制造对象。抽象方法只声明, 不实现。具体的实现由继承它的子类来实现。

	```java
	public abstract class Shape{
		// 抽象的方法, 注意没有大括号, ()后面直接分号结尾
		// 有abstract方法的类必须是abstract
		public abstract void draw();
	}
	```

	接口, 让其他类能够有接口的方法

	```java
	public interface Cell{
		// 不需要显示写abstract
		void draw(Graphics g, int x, int y, int size);
	}

	public class Fox extends Animal implements Cell{
		@Override
		public void draw(...){
			// ...
		}

		public void run()
		{

		}
	}
	```

	<br>

	抽象类可以有非抽象的方法(具体实现), 接口是纯抽象类, 只有抽象方法

	一个子类只能存在一个父类, 但是可以存在多个接口。

	<br>

###	MVC 开发模型

*	数据模型、表现、控制, 三者分离
	
	M, Model, 模型, 保存和维护数据, 还可以 通知 View 进行界面的更新.

	V, View, 表现, 从 Model 获得数据, 并以此画出表现(界面). View 是被动的, 只有在 Model 通知 View 之后, View才会去Model取数据, 并画出来.

	C, Control, 控制, 得到用户输入, 以此调整数据. C 和 V 并不直接交互. C只能更新Model中的数据, 也就是说, 用户在界面上所作的操作, 不会直接修改界面上的显示. 而是先去修改后台的数据, 再由Model通知View, 再整体重画.
	```

	<br>

###	多线程

*	创建线程的方式, 继承 Thread 类, 实现 Runnable 接口

	start(), run(), stop(), destroy()

	新建 --- 就绪 --- 运行 --- 阻塞 --- 运行 --- 终止

	[40 个 Java 多线程问题总结](https://juejin.im/entry/58f1d35744d904006cf14b17)

	[Java多线程学习](https://blog.csdn.net/evankaka/article/details/44153709)

	[Java 多线程编程](http://www.runoob.com/java/java-multithreading.html)

	<br>

###	错误和异常

*	分类

	```
	ArrayIndexOutOfBoundsException
	OpenFileException
	AllocateMemoryException
	LoadFileException

	OutOfMemoryError
	```

	![clipboard.png](https://segmentfault.com/img/bVbr9dP)

	<br>

*	处理方式

	```java
	try{

	}
	catch(ArrayIndexOutOfBoundsException e){

	}
	```

	<br>

###	GC, 垃圾回收机制

*	[Wikipedia, GC](https://zh.wikipedia.org/wiki/垃圾回收_(計算機科學))

	某个对象在未来的程序运行中, 将不会被访问, 就可以回收它的内存

	<br>

*	回收方法，策略

	引用计数收集器, 当有其他数据与其相关时则加一, 反之相关解除时减一, 最后计数为 0 的对象可以回收

	跟踪收集器, 定期对若干根储存对象开始遍历, 对与其相关的对象进行标记, 最后, 没有被标记的对象就可以回收

	<br>

##	C

###	存储区

*	栈 stack

	局部变量, 函数参数

	<br>

*	全局/静态 存储区

	全局变量, 静态全局变量, 静态局部变量

	若没有手动初始化, 则会自动初始化为0

	<br>

*	堆 heap

	new --- delete / malloc --- free

	<br>

*	常量存储区

	存放字符串常量和const修饰的全局变量

	<br>

###	c的源文件经过了预处理, 编译, 汇编, 链接, 每一步的作用是什么。

*	预处理Pre Pocess：包含头文件, 条件编译, 宏替换

	<br>

*	编译：检查语法错误. 检查无误后, 将代码翻译成汇编语言

	<br>

*	汇编：将汇编语言转化成二进制代码表示的目标文件. 每一个源文件(.c)产生一个目标文件(.obj)

	<br>

*	链接：与库函数进行链接, 形成可执行文件

	<br>

*	整体过程

	预处理 --- 编译 --- 汇编 --- 链接 --- 装载 --- 运行

	malloc, 分配内存, 是在 `运行` 这一阶段。即在 heap 上动态分配

	<br>

*	[gcc编译程序的四个阶段（预处理-编译-汇编-链接）](http://blog.csdn.net/qq_31108501/article/details/51841983)

	<br>

*	[C++ 预处理、编译、汇编、链接](http://blog.csdn.net/u011974126/article/details/47957503)

	<br>

*	[C语言编译过程详解](https://www.cnblogs.com/CarpenterLee/p/5994681.html)

	<br>

###	指针

*	指向二维数组的指针

	```c
	int a[4][2];
	int (*p) [2];

	p = a;
	p[3][1];
	```

	`[]` 的优先级高于 `*`, 所以要加括号

	<br>

*	二级指针

	```c
	void getMemory(char **p){
		*p = (char *)malloc(100);
	}

	int main(){
		char *str = NULL;
		getMemory(&str);
		strcpy(str, "Thurs");
		strcat(str+2, " day");

		printf("%s\n", str);
		return 0;
	}
	```

	<br>

	首先 `str` 被分配了100字节的空间, 然后在 str 开头粘贴了 `Thurs`, 接着, 由于 `strcat` 总是先找到末尾再粘贴, 所以 `day` 不会覆盖 `urs`

	<br>

###	补码

*	正数与原码和反码相同。对于负数, 以 `-1` 为例

	```
	1)先写出原码, `1000 0001`
	2)符号位不变, 其余各位取反, `1111 1110`
	3)最后 +1, `1111 1111`
	```

	<br>

*	数据类型在内存中的表达形式

	```
	整数：二进制数（补码）, 可以直接在加法器里面做加法
	浮点数：要进行编码
	```

	<br>

###	结构体

*	结构体内定义指针

	```c
	typedef struct{
		int val;
		struct Node *lchild, *rchild;
	}Node;

	Node root = {1, NULL, NULL};
	```

	<br>

	```c
	struct node{
		int val;
		struct Node *lchild, *rchild;
	};

	struct node root = {1, NULL, NULL};
	```

	<br>

###	const

*	`const` 在 `*` 之前, 意思是对 `i` 只读

	```c
	/* const 在 * 之前, 意思是 对 i 只读
	** 可以通过 *p 读取i的值, 但不能通过 *p 修改i的值
	** 另外, 指针作为函数参数时, 这样写 (const int * p)
	*/
	int i = 1;
	const int * p1 = &i;
	int const * p2 = &i;
	```

	<br>

*	const 在 * 的后面, 意思是 指针 不能指向其他地址

	```
	/* const 在 * 的后面, 意思是 指针 不能指向其他地址
	** p3 被绑定到了 j, 就无法再指向其他地址
	** 可以通过p3来读写j的值
	*/
	int j = 2;
	int * const p3 = &j;
	*p3;			// ok
	*p3 = 3;		// ok

	int k = 123;
	p3 = &k;		// error
	```

	<br>

###	malloc

*	用法

	```c
	int *a = (int *)malloc( 10*sizeof(int) )
	```

	`man malloc` 可以看到参数要求是`(size_t size)`, 所以实参是`(10*sizeof(int))`, 表示申请到了`10*4=40`个字节的空间, 同样的也可以`40*sizeof(char)`, 或者直接写`40`
	可以看到返回类型是 `void *` , 这也就解释了为什么要在前面加上`(int *)`, 由此划分空间, 来区分类型

	<br>

###	sizeof()

*	`sizeof()`是静态的, 程序编译完成后已经定下来, 直接填进去了, 并不会真的去做计算

	```c
	int a = 1;

	printf("%d\n", sizeof(a++));	// 4
	printf("%d\n", a);		// 1, sizeof()是静态的, 程序编译完成后已经定下来, 直接填进去了, 并不会真的去做a的++

	printf("%d\n", sizeof(a + 2.0));// 8, 已经转换成了double
	printf("%d\n", sizeof(double));	// 8
	return 0;
	```

	<br>

###	define 和 const 的区别

*	编译器处理方式不同

	`define` 宏是在预处理阶段展开, `const` 常量是编译运行阶段使用.

	<br>

*	类型和安全检查不同

	define宏没有类型, 不做任何类型检查, 仅仅是展开. const常量有具体的类型, 在编译阶段会执行类型检查.

	<br>

*	存储方式不同

	define宏仅仅是展开, 有多少地方使用, 就展开多少次, 不会分配内存. const常量会在内存中分配(堆或栈).

	<br>

###	其他

*	全局 static, 初始化为 0, 作用域是文件内部, 放在全局/静态 存储区, 生命周期从程序开始到程序结束

	<br>

*	局部 static, 局部作用域

	<br>

*	extern 全局 (extern可省略)

	<br>

*	宏 --- 字符替换

	<br>

*	main可以作为变量名

	<br>

*	浮点数 --- 不可以用 `==` 作为判断条件

	<br>

##	C++

###	虚函数

*	函数名前面加了 `virtual` 的函数叫做虚函数

	<br>

*	用于 `多态` (即 `动态绑定`, `覆盖Override`, 运行的时候根据实例对象来调用方法)

	```cpp
	class Animal {
	public:
		void run(){
			cout << "That animal is running\n";
		}
		virtual void eat(){
			cout << "That animal is eating\n";
		}
	};
	class Dog : public Animal{
	public:
		void run(){
			cout << "The dog is running\n";
		}
		void eat(){
			cout << "The dog is eating\n";
		}
	};
	int main(){
		// 父类 `Animal` 类型的 `指针` 可以管理子类对象
		// 如果方法名前面有 virtual, 则可以动态绑定
		Animal * animal = new Dog();
		animal->run(); // That animal is running, 隐藏子类方法
		animal->eat(); // The dog is eating, 子类方法覆盖父类, 多态

		// 注意指针才可以, 普通变量形式仍然会隐藏子类方法
		Animal ani = Dog();
		ani.eat(); // That animal is eating, 隐藏子类方法
		return 0;
	}
	```

	<br>

	父类方法被声明为 `virtual` 后, 直接/间接子类中的这个方法都会变成 `virtual`, 也即子类中的 `virtual` 可以省略, 但最好还是写上去

	<br>

	[什么是C++虚函数、虚函数的作用和使用方法](http://c.biancheng.net/cpp/biancheng/view/244.html)

	[虚函数表](http://www.cnblogs.com/CPYER/p/3399468.html)

	<br>

###	纯虚函数

*	纯虚函数只有声明, 没有实现, 相当于接口规范。含有纯虚拟函数的类称为抽象类, 它不能生成对象(不能放在等号右边), 但可以声明指向实现该抽象类的具体类的指针或引用。

	```cpp
	class Flyable {
	public:
		virtual void fly() = 0; // 纯虚函数, 只有声明, 后接 = 0
		virtual void run() = 0; 
	};

	class Bird : public Flyable{
	public:
		void fly(){
			cout << "Bird can fly\n"; // 子类只有实现纯虚函数才能实例化
		}
	};

	class Superman : public Flyable{
	public:
		void fly(){
			cout << "Superman can fly\n";
		}
		void run(){
			cout << "Superman is running\n";
		}
	};

	int main(){
		Flyable * f1 = new Bird();
		f1->fly(); // 出错, 因为没有实现所有的纯虚函数, 所以仍然是抽象类, 无法实例化
		Flyable f2 = new Superman();
		f2->fly(); // Superman can fly
		return 0;
	}
	```

	<br>

	定义纯虚函数的目的在于, 使派生类仅仅只是继承函数的接口。纯虚函数的意义, 让所有的类对象（主要是派生类对象）都可以执行纯虚函数的动作, 但类无法为纯虚函数提供一个合理的缺省实现。所以类纯虚函数的声明就是在告诉子类的设计者, “你必须提供一个纯虚函数的实现, 但我不知道你会怎样实现它”。

	<br>

	[C++中虚函数的作用是什么？它应该怎么用呢？](https://www.cnblogs.com/to-creat/p/5897465.html)

	<br>

###	new 和 malloc 区别

*	返回类型安全性

	`new` 操作符内存分配成功时, 返回的是对象类型的指针, 类型严格与对象匹配, 无须进行类型转换, 故 `new` 是符合类型安全性的操作符。而 `malloc` 内存分配成功则是返回 `void *`, 需要通过强制类型转换将 `void *` 指针转换成我们需要的类型。

	<br>

	类型安全很大程度上可以等价于内存安全, 类型安全的代码不会试图方法自己没被授权的内存区域。关于 `C++` 的类型安全性可说的又有很多了

	<br>

*	[细说new与malloc的10点区别](https://www.cnblogs.com/QG-whz/p/5140930.html)

	<br>

*	[C++ 自由存储区是否等价于堆？](http://www.cnblogs.com/QG-whz/p/5060894.html)

	<br>

##	前端

###	JavaScript

*	选择器

	```javascript
	// 按ID查找
	document.getElementById('xxx');

	// 按tagname查找
	document.getElementsByTagName('xxx');

	// classname
	document.getElementsByClassName('xxx');
	```

	<br>

*	jQuery, 选择器是 `jQuery` 的核心

	```javascript
	// DOM 操作
	var ele = document.getElementById('id1');
	var divlist = document.getElementsByTagName('div');

	// jQuery 的写法
	// 返回一个 jQuery 对象, 即若 id1 存在, 那么返回 [<div id="id1">...</div>]
	// 若不存在, 则返回 []
	var ele = $('#id1');

	// jQuery 对象和 dom 对象相互转化
	var eledom = ele.get(0);
	ele = $(eledom);

	// 按 class 查找
	var a = $('.red.green'); // 多个 class 时中间没有空格

	// 按属性查找
	var email = $('[name=email]'); // 找出<??? name="email">
	var passwordInput = $('[type=password]'); // 找出<??? type="password">

	var icons = $('[name^=icon]'); // 找出所有name属性值以icon开头的DOM
	var names = $('[name$=with]'); // 找出所有name属性值以with结尾的DOM

	// 组合查找
	var emailInput = $('input[name=email]');
	// 找到所有 input 中的 name="email" 的属性
	// 不会找出 <div name="email">

	// 多项选择器(不会重复选择)
	$('p,div'); // 把<p>和<div>都选出来
	$('p.red,p.green'); // 把<p class="red">和<p class="green">都选出来
	```

	<br>

*	正则表达式

	```javascript
	`\d` 数字
	`\w` 字母或数字
	`.`  至少 1 个任意字符
	`*`  至少 0 个任意字符
	`\d{3}` 匹配 3 个字符
	`[0-9a-zA-Z\_]` 匹配一个数字, 字母或者下划线
	var re1 = /^\d{11}$/;
	re1.test('12345678');	// false
	```

	<br>

*	AJAX, Asynchronous JavaScript and XML, 意思就是用 JavaScript 执行异步网络请求

	AJAX请求是异步执行的, 也就是说, 要通过回调函数获得响应

	```javascript
	function success(text) {
		var textarea = document.getElementById('test-response-text');
		textarea.value = text;
	}

	function fail(code) {
		var textarea = document.getElementById('test-response-text');
		textarea.value = 'Error code: ' + code;
	}
	
	var request = new XMLHttpRequest(); // 新建XMLHttpRequest对象
	request.onreadystatechange = function () { // 状态发生变化时, 函数被回调
		if (request.readyState === 4) { // 成功完成
			// 判断响应结果:
			if (request.status === 200) {
				// 成功, 通过responseText拿到响应的文本:
				return success(request.responseText);
			} else {
				// 失败, 根据响应码判断失败原因:
				return fail(request.status);
			}
		} else {
			// HTTP请求还在继续...
		}
	}

	// 发送请求:
	request.open('GET', '/api/categories');
	request.send();
	```

	<br>

##	Python

*	如何管理内存, 垃圾回收

	引用计数, del对象

	<br>

###	多进程与多线程

*	`Unix/Linux` 推荐多进程, 提供了一个 `fork()` 系统调用(`System call`)

	<br>

	`pid = fork()`, 调用一次返回两次, 子进程中返回的 `pid == 0`, 父进程中返回的是子进程的 `pid > 0`, `ppid = getppid()` 可以得到父进程的 `pid`

	```python
	import os
	# 得到当前进程的 pid
	print( os.getpid() )
	pid = os.fork()
	if pid == 0:
		print('This is child process %s, parent is %s' % (os.getpid(), os.getppid()))
	else:
		print('This is parent process %s, child is %s' % (os.getpid(), pid))
	```

	<br>

	结果

	```
	17420
	This is parent process 17420, child is 17421
	This is child process 17421, parent is 17420
	```

	<br>

*	`Windows` 没有 `fork()`, `Python` 多进程需要使用 `multiprocessing`

	```python
	from multiprocessing import Process
	import os

	def proc(name):
		print('child process %s, pid = %s' % (name, os.getpid()))

	p = Process( target=proc, args=('test',) )
	print('child process start')
	p.start()
	p.join()
	print('child process end')
	```

	<br>

	结果

	```
	child process start
	child process test, pid = 17491
	child process end
	```

	<br>

	创建子进程时, 只需要传入待执行函数 `target` 和函数的参数, 创建一个 `Process` 实例, 用 `start()` 方法启动

	`join()` 方法可以等待子进程结束后再继续往下运行, 通常用于进程间的同步。

	<br>

*	多线程. 进程是由若干线程组成的, 一个进程至少有一个线程, 线程是操作系统直接支持的基本执行单元.

	启动一个线程就是把一个函数传入并创建 `Thread` 实例, 然后调用 `start()` 开始执行

	```python
	import time, threading
	def loop():
		print('%s is running' % threading.current_thread.name)

	print( '%s is running' % threading.current_thread().name )
	t = threading.Thread(target=func, name='myThread')
	t.start()
	t.join()
	print( '%s ended' % threading.current_thread().name )
	```

	<br>

*	区别: 多进程中, 同一个变量, 各自有一份拷贝存在于每个进程中, 互不影响, 而多线程中, 所有全局变量都由所有线程共享, 所以, 任何一个变量都可以被任何一个线程修改, 因此, 线程之间共享数据最大的危险在于多个线程同时改一个变量, 把内容给改乱了。

	多线程共享的内容: 虚拟地址空间,只读代码块,读、写数据, 堆(全局, 静态), 打开的文件集合

	<br>

*	锁

	```python
	balance = 0
	def change_balance(n):
		global balance
		balance += n
		balance -= n

	lock = threading.lock()

	def run_thread(n):
		for i in range(10000):
			# 用之前先获得 balance 等全局变量的独占权
			lock.acquire()
			try:
				change_balance(n)
			finally:
				# 用完后释放锁
				lock.release()
	```

	<br>

###	Java Python 区别

*	Java 静态类型语言, 编译的时候就确定了数据类型了, 编写代码的时候要明确变量的数据类型

	Python 动态类型语言, 运行期间才检查数据类型

	<br>

*	语法不一样, Java 用大括号划分代码块, Python 用缩进划分代码块

	Java 分号结尾, Python 不需要

	<br>

##	数据结构

###	链表

*	插入

	<br>

*	删除

	<br>

###	二叉树

*	LCA

	<br>

*	红黑树

	<br>

*	AVL

	<br>

##	算法

###	排序

*	几个考点: 复杂度, 稳定性, 实现

	<br>

*	冒泡, 最好 O(n), 最坏 O(n^2)

	```cpp
	// 升序
	void bubble_sort(int a[], int len){
		for(int i=0; i < len; i++ ){
			for( int j = len - 1; j > i; j-- ){
				if( a[j] < a[j-1] ){
					swap(a[j], a[j-1]);
				}
			}
		}
	}

	int main(){
		const int len = 8;
		int a[len]={4, 2, 5, 1, 3, 2, 5, 1};

		bubble_sort(a, len);
		for( int i = 0; i < len; i++){
			cout << a[i] << '\t';
		}
		return 0;
	}
	```

	<br>

*	快排, 最坏 O(n^2), 平均 O(nlgn)

	```cpp
	int a[MAXSIZE] = {4, 2, 6, 3, 1, 5, 7};

	int partQuickSort(int left, int right){
		int i = left, j = right;
		int key = a[i];
		while( i < j ){
			while( i < j && a[j] > key ){
				j--;
			}
			if( i < j ){
				// a[j] < key, 换到左边
				a[i++] = a[j];
			}

			while( i < j && a[i] < key ){
				i++;
			}
			if( i < j ){
				// a[i] > key, 换到右边
				a[j--] = a[i];
			}
		}

		int mid = i;
		a[mid] = key;
		return mid;
	}

	/*
	以a[left]为中轴key, 把所有小于key的都放到它的左边, 大的放到右边。
	中轴的位置就固定了。
	再对左边这一块和右边这一块, 做同样的处理。
	*/
	void quickSort( int left, int right ){
		if(left < right){
			int mid = partQuickSort(left, right);
			quickSort(left, mid - 1);
			quickSort(mid + 1, right);
		}
	}
	```

	<br>

*	插入, 最好 O(n), 最坏 O(n^2)

	```cpp
	// 升序
	void insert_sort(int a[], int len){
		for(int i = 1; i < len; i++ ){
			int j = i;
			int key = a[j];
			// 把 key 插到正确的位置
			while( j > 0 && a[j-1] > key ){
				a[j] = a[j-1];
				j--;
			}
			a[j]=key;
		}
	}
	```

*	归并, O(n^2)

<br>

###	查找

*	二分, 序列必须有序

	```cpp
	// 递归
	int bsearch(int a[], int left, int right, int key){
		if( left <= right ){
			int mid = (left + right) / 2;
			if( key < a[mid] ){
				return bsearch(a, left, mid - 1, key);
			}
			else if( key > a[mid] ){
				return bsearch(a, mid + 1, right, key);
			}
			else{
				return mid;
			}
		}
		return -1;
	}

	// 非递归
	int bsearch(int a[], int left, int right, int key){
		while( left <= right ){
			int mid = (left + right) / 2;
			if( key < a[mid] ){
				right = mid - 1;
			}
			else if( key > a[mid] ){
				left = mid + 1;
			}
			else{
				return mid;
			}
		}
		return -1;
	}
	```

	<br>

###	字符串匹配

*	KMP

	<br>

*	BM

	<br>

###	动态规划

*	最大连续子列和

	<br>

*	

###	全排列

*	next_permutation

	<br>

###	其他

*	最大公因数 gcd, 最小公倍数 lcm

	```cpp
	// PAT_B_1062, 1034, PAT_A_1081

	// 最大公因数, the Greatest Common Divisor
	int get_gcd(int a, int b){
		if( b == 0 ){
			return a;
		}
		else{
			return get_gcd(b, a % b);
		}
	}

	// 最小公倍数, the Lowest Common Multiple
	int get_lcm(int a, int b){
		int gcd = get_gcd(a, b);
		if( gcd != 0 ){
			return a * b / gcd;
		}
		else{
			return 0;
		}
	}
	```

*	素数

*	Fib

<br>

##	数据库

*	数据库事务(Transaction)的 ACID 特性

	原子性(Atomicity), 一致性(Consistency), 隔离型(Isolation), 持久性(Durability)

	*	原子性(A)是指事务中的操作不可拆分, 只允许全部执行或者全部不执行

	*	一致性(C)指事务的执行不能破坏数据库的一致性, 一致性也称为完整性。一个事务在执行后, 数据库必须从一个一致性状态转变为另一个一致性状态

	*	隔离性(I)指并发的事务相互隔离, 不能互相干扰

	*	持久性(D)指事务一旦提交, 对数据的状态变更应该被永久保存

*	数据库事务隔离级别有4个

	```
	# 由低到高依次为
	Read uncommitted, 读到了未提交的事物, 只是 add 还没有 commit
	Read committed, 读到了上一次的commit, 也就是说还没有更新 最新的commit
	Repeatable read, 保证读取最新的 commit, 为此, 读取的时候不允许提交
	Serializable, 要求有很高的实时同步性
	# 这四个级别可以逐个解决脏读 、不可重复读 、幻读 这几类问题
	```

*	锁（并发控制的手段）

*	关系数据模型的三个组成部分

	数据结构, 对数据的操作, 完整性约束

*	参考链接

	[数据库事务、隔离级别、锁的理解与整理](https://blog.csdn.net/feeltouch/article/details/78369536)

##	SQL

*	CRUD

	Create, Read, Update, and Delete

*	过程

	```sql
	1.首先连接到数据库
	  conn = sqlite.connect('test.db')
	2.建立游标 cursor
	  cursor = conn.cursor()
	3.建立表
	  create table user (id int, name varchar(20), score int )
	4.insert into 插入数据, 注意占位符是 ?
	  insert into user (id, name) values(1, "Alice", 88)
	  insert into user (id, name) values(2, "Bob", 89)
	  insert into user (id, name) values(3, "Cindy", 88)
	5.select * from user where 查找数据
	  select * from user where id between 1 and 3 order by score asc
	6.cursor.close()
	7.conn.commit()
	8.conn.close()
	```

*	column, 列, 字段

	```sql
	select * from user
	select col1, col2 from user
	```

*	下面以这个表格 `customers` 为例, 展示 SQL 的语法

	| --- | --- | --- | --- | --- | --- |
	| id  | name | age | city | postalcode | country |
	| 1 | Alfreds | 25 | Berlin | 12209 | Germany |
	| 2 | Ana | 15 | Mexico | 05021 | Mexico |
	| 3 | Antonio | 20 | Mexico | 05023 | Mexico |
	| 4 | Thomas | 30 | London | WA11DP | UK |
	| 5 | Berglunds | 35 | Lulea | S-958-22 | Sweden |

*	where 条件选择

	```sql
	select * from customers where country='Germany' and city='Berlin'
	```

*	order by 排序

	```sql
	select * from customers order by country
	```

*	插入

	```sql
	insert into customers (name, age, city, postalcode, country) values ('Bart', 10, 'LA', '4006', 'USA')
	```

*	更新

	```sql
	update customers set name = 'Smith', city = 'Paris' where id = 5
	```

*	删除

	```sql
	delete from customers where name = 'Berglunds'
	```

*	limit/top 不返回全部结果, 只返回有限数量的记录

	```sql
	# SQL
	select top 3 from customers
	# MySQL
	select * from customers limit 3
	```

*	最大最小值

	```sql
	select min(age) from customers
	```

*	统计 count, distinct

	```sql
	# 统计有多少个不同的国家
	select count(distinct country) from customers
	```

*	平均值

	```sql
	select avg(age) from customers
	```

*	求和

	```sql
	select sum(age) from customers
	```

*	通配符

	```sql
	# SQL
	select * from customers where name like 'B%'
	# sqlite
	select * from customers where name like 'B*'
	```

*	选择范围

	```sql
	# 离散
	select * from customers where country in ('Germany', 'France')
	# 连续
	select * from customers where age between 10 and 20
	```

*	连接表格

	```
	inner join, (A ∩ B)
	left join, (A ∩ B) U A
	right join, (A ∩ B) U B
	full outer join, (A U B)
	```

*	[参考资料](https://www.w3schools.com/sql/)

##	计算机网络

###	HTTP 状态码

*	2xx: Successful responses

	*	200 OK

		<br>

*	3xx: Redirection messages

	*	301 Moved Permanently, 永久转移

		This response code means that the URI of the requested resource has been changed permanently. Probably, the new URI would be given in the response.

		<br>

	*	307 Internal Redicrection, 浏览器自动重定向, HSTS 会用到

*	4xx: Client error responses

	*	400 Bad Request, 非法请求

		This response means that server could not understand the request due to invalid syntax.

		<br>

	*	403 Forbidden, 未认证, 权限不够

		The client does not have access rights to the content, i.e. they are unauthorized, so server is rejecting to give proper response. Unlike 401, the client's identity is known to the server.

		<br>

	*	404 Not Found, 没有相应的资源, 路径不对

		The server can not find requested resource. In the browser, this means the URL is not recognized. In an API, this can also mean that the endpoint is valid but the resource itself does not exist. Servers may also send this response instead of 403 to hide the existence of a resource from an unauthorized client. This response code is probably the most famous one due to its frequent occurence on the web.

		<br>

	*	405 Method Not Allowed, 非法的请求方式

		The request method is known by the server but has been disabled and cannot be used. For example, an API may forbid DELETE-ing a resource. The two mandatory methods, GET and HEAD, must never be disabled and should not return this error code.

		<br>

*	5xx: Server error responses

	*	500 Internal Server Error, 服务器内部错误

		The server has encountered a situation it doesn't know how to handle.

		<br>

	*	501 Not Implemented, 请求方法未实现

		The request method is not supported by the server and cannot be handled. The only methods that servers are required to support (and therefore that must not return this code) are GET and HEAD.

		<br>

*	参考资料

	https://developer.mozilla.org/en-US/docs/Web/HTTP/Status

	<br>

###	GET 和 POST 区别

*	幂等

	GET为请求数据, 没有副作用, 每次请求的效果都相同。

	POST为修改数据, 相对GET来讲没有那么安全（因为要修改数据）。

	<br>

*	安全性

	GET 通过 URL 传输数据, 容易在日志记录中留下私密数据, 隐蔽性没有POST好。

	<br>

*	长度限制。

	一般通过GET方式传输数据, 由于Web Server和浏览器限制, URL长度限制传输的数据有限(根据Web Server配置和浏览器不同, 一般为2kB~8kB)

	而POST通常可以忽略限制(实际上根据Web Server配置也还是有限制的, 一般是2G)

	http://stackoverflow.com/questions/2659952/maximum-length-of-http-get-request

	<br>

###	TCP 连接

*	三次握手

	![TCP Connect](https://segmentfault.com/img/bVbsUGi)

	<br>

*	过程

	*	服务器 B 处于 LISTEN 状态, 监听端口, 等待请求

	*	客户端 A 的 TCP 进程首先创建 TCB (传输控制块, 存储了每一个连接中的重要信息, srcPort, dstPort, srcIP, destIP, seq, ack)。 然后向 B 发出连接请求报文段(传输层是段, 网络层是包, 链路层是帧)。 此时 【 SYN=1, seq=x 】, 不携带数据, 但是消耗一个序号。接着进入 SYN-SENT状态。

	*	B 收到连接请求后, 如果同意连接, 则向A发送确认(ACK), 此时 【 SYN=1, ACK=1, ack=x+1, seq=y 】, ACK是确认标志, ack是确认号。这个报文段不带数据, 但是消耗一个序号。服务器进入 SYN-RCVD 状态

	*	A 收到 B 的确认后, 还要向 B 确认自己收到了。此时 【 ACK=1, ack=y+1, seq=x+1 】, 这个ACK报文段可以带数据。接着 A 进入ESTABLISHED  状态。

	*	B 收到 A 的确认后, 也进入 ESTABLISHED 状态。

	<br>

*	为什么三次握手, 而不是两次？也就是说, `B` 在第一次收到 `A` 的 `SYN` 之后, 没有立刻进入 `ESTABLISHED`, 而是等到 `A` 再来一次 `ACK` 才建立连接, 为什么要这样设计？

	答：防止已经失效的连接请求(比如在某个网络滞留了很久), 突然又传到了 `B` , 从而产生错误, 造成 `B` 的资源浪费.

	<br>

	考虑这样一种情况: `A` 的第一次 `SYN` 被拦截了。然后 `A` 又发了一次 `SYN`, `B` 收到, 并且完成后续的 `握手 --- 数据传输 --- 挥手`。

	此时 `A` 的第一次 `SYN` 又被放了出来, 并传到 `B`, 如果只需要 `2` 次握手, 那么此时 `B` 就会直接进入 `ESTABLISHED`

	而这个时候 `A` 都已经关机了, 不会发数据过来了, `B` 就在 `ESTABLISHED` 中苦苦等待 `A`, 浪费很多资源。

	如果是3次握手, 那么 `B` 只会进入 `SYN-RCVD` 状态, 一段时间后 (比 `ESTABLISHED` 要短, 而且不会占用那么多资源), 会自动取消连接

	<br>

*	SYN Flood

	`SYN Flood` 是一种广为人知的 `DoS` (拒绝服务攻击) , 是 `DDoS` (分布式拒绝服务攻击) 的方式之一, 这是一种利用 `TCP` 协议缺陷, 发送大量伪造的 `TCP` 连接请求, 从而使得被攻击方资源耗尽 (`CPU`满负荷或内存不足) 的攻击方式。

	<br>

	假设一个用户向服务器发送了 `SYN` 报文后突然死机或掉线, 那么服务器在发出 `SYN+ACK` 应答报文后是无法收到客户端的 `ACK` 报文的 (第三次握手无法完成) , 

	这种情况下服务器端一般会重试 (再次发送 `SYN+ACK` 给客户端) 并等待一段时间后丢弃这个未完成的连接, 这段时间的长度我们称为 `SYN Timeout`, 一般来说这个时间是分钟的数量级 (大约为30秒 - 2分钟).

	一个用户出现异常导致服务器的一个线程等待1分钟并不是什么很大的问题, 但是, 如果有一个恶意的攻击者大量模拟伪造这种情况, 服务器端将会维护一个非常大的半连接列表, 从而消耗非常多的资源

	数以万计的半连接, 即使是简单的保存并遍历也会消耗非常多的 `CPU` 时间和内存, 何况还要不断对这个列表中的 `IP` 进行 `SYN+ACK` 的重试

	实际上如果服务器的 `TCP/IP` 栈不够强大, 最后的结果往往是堆栈溢出崩溃, 

	即使服务器端的系统足够强大, 服务器端也将忙于处理攻击者伪造的 `TCP` 连接请求而无暇理睬客户的正常请求 (毕竟客户端的正常请求比率非常之小) , 此时从正常客户的角度看来, 服务器失去响应, 无法对正常客户进行服务

	这就是 `SYN Flood` 攻击

	<br>

	防御措施: 缩短 `SYN Timeout`, 增加 `IP` 黑名单, 使用 `CDN`

	<br>

###	TCP 断开

*	断开, 4次挥手 (4-way handshake, connection termination)

	![TCP Close](https://segmentfault.com/img/bVbsUGi)

	<br>

*	MSL, Maximum Segment Lifetime, 最长报文段寿命

	`A` 发出的最后一个 `ACK` 可能会丢失. 而此时 `B` 还在等待这个 `ACK`, 如果 `B` 一直没有收到, 则会给 `A` 发一个 `FIN + ACK`, 通知 `A` 刚才那个没收到, 从 `A` 发出 `ACK` 到 `B` 发出 `FIN + ACK` 需要 `2MSL`, 如果 `2MSL` 时间里面 `A` 都没有收到 `B` 的回复, 就认为自己的 `ACK` 已经送达 `B`, 所以 `A` 可以安心关闭了

	<br>

	而且, `2MSL` 后, 可以使本次连接所产生的所有报文段都从网络上消失 (`TTL, Time To Live`), 以后建立新的连接, 就不会和旧的连接混淆

	<br>

##	趋势科技

###	安卓

*	网络请求具体过程, 步骤, 代码

	<br>

*	用了异步吗, 为什么（网络慢的时候不会卡界面）

	<br>

*	MainActivity, 点击, 进入新的 Activity 这中间发生了什么, 怎么传递的消息？

	Intent

	<br>

###	Python

*	为什么选 Flask, 什么叫做轻？其他框架有看过吗？

	<br>

*	为什么要做这个网站？

	<br>

*	把 vue 和 echarts 放到 html-body 前面

	<br>

###	网络和安全

*	https 有什么作用, https具体连接过程是怎么样的

	<br>

*	用 let's encrypt 的 https 证书需要注意哪些事情？有什么限制吗？为什么设置 60 天的有效期, 过期了要重新延长？证书有效期是什么概念？有效期过了会导致什么问题？

	<br>

*	输入 URL 到页面展示, 中间发生了什么？授权解析服务器

	<br>

*	拿到端口号后, 谁跟谁之间建立了什么连接？

	<br>

*	有哪些 request 的方法？GET, POST, PUT, DELETE 还有吗？RESTful API？

	<br>

*	GET 和 POST 有什么区别？

	<br>

*	GET对URL的限制是哪里限制的？(Server 和 浏览器 都有限制)

	<br>

*	HTTP headers的作用, 比如 Connection: keep-alive 是干什么用的？重用是什么概念, 是谁的重用？

	客户端和服务器之间用于传输HTTP数据的TCP连接不会关闭, 如果客户端再次访问这个服务器上的网页, 会继续使用这一条已经建立的连接 

	<br>

*	HSTS？

	<br>

###	JavaScript, 前端

*	javascript, setTimeout() 的用法

	```javascript
	console.log(1)
	for( let i = 0; i < 5; i++ ){
		setTimeout(function(){console.log(2);}, 1000);
	}
	console.log(3);
	```

	输出是什么（1 3 2 2 2 2 2）

	异步, 不会等

	https://www.liaoxuefeng.com/wiki/1022910821149312/1023024413276544

	<br>

*	前端怎么向后端发起请求

	axios, jQuery, AJAX 是怎么写的

	<br>

###	建议

*	基础要扎实

	体系结构, 操作系统, 网络, 语言, 数据结构算法, 框架, 应用

	<br>

*	集中, 专攻, 而且要体现在简历上, 让面试官知道问什么

	如果要做 Java 就专攻 Java, SSM/SSH 实践好, 理解好

	<br>

*	Python 如果要做, 也要深入, 不要皮毛

	<br>

##	其他

*	[牛客网面试经历 (视频面试)](https://blog.mythsman.com/2017/04/19/1/)

*	项目经历

	<br>

*	自我介绍(中英文)

	<br>
