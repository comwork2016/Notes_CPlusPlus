.. _fucntions:

函数
==========

函数重载
^^^^^^^^^^^

+ 顶层const不影响传入函数的对象，一个拥有顶层const形参无法和另一个没有顶层const的形参区分开来。

::

	Record lookup(Phone);
	Record lookup(const Phone);//重复声明
	
	Record lookup(Phone*);
	Record lookup(Phone* const);//重复声明		

+ 如果形参是某种类型的指针或引用，此时通过区分其指向的是常量对象还是非常量对象可以实现函数重载，此时的const是底层的。

::

	Record lookup(Account&);  
	Record lookup(const Account&);//新函数

	Record lookup(Phone*);  
	Record lookup(const Phone*);//新函数


函数作用域
^^^^^^^^^^

+ 如果我们在内层作用域中生命名字，他将隐藏外层作用域中声明的同名实体。在不同的作用域中无法重载函数名：

::

	string read();
	void print(const string&);
	void print(double);//重载print
	
	void fooBar(int ival)
	{
		bool read = false;//新作用域：隐藏了外层的read
		string s = read();//错误：read是一个布尔值
		void print(int);//新作用域，隐藏了之前的print
		print("value:");//错误，print(cosnt string&)被隐藏了
		print(ival); //正确：print(int)
		print(3.14); //正确：print(int)
	}
