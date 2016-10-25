.. _classes:

类
=======

类成员
----------

+ 定义在类内部的成员函数是自动 **inline** 的。
+ const成员函数:默认情况下，this的类型是指向类类型的非常量版本的指针，如 Sales * const this; 当类中的成员函数中的参数列表后面加了const之后，此时this指针是一个指向常量的指针(cosnt Sales * const this;)，此时类中的成员变量将不能在该成员函数中改变。

构造函数
---------------

+ 委托构造函数：一个委托构造函数 使用它所属的类的其他构造函数执行它自己的初始化过程。
+ 转换构造函数：在要求隐式转换的程序上下文中，我们可以通过将构造函数声明为 **explicit** 加以阻止。

::

	class Sales{
	public:
		Sales() = default;
		Sales(const string &s,unsigned n, double p):bookNo(s),units_sold(n),revenue(p*n){}
		explicit Sales(const string &s):bookNo(s){}
		explicit Sales(std::istream&);
	}

+ explicit只对一个实参的构造函数有效。需要多个实参的构造函数不能用于执行隐式转换，所以无须将这些构造函数指定为explicit的。
+ 只能在类内声明构造函数时使用explicit关键字，在类外部定义时不应重复。
+ explicit构造函数只能用于直接初始化

::

	Sales item1(null_book);// 正确：直接初始化
	Sales item2 = null_book; // 错误：不能将explicit构造函数用于拷贝形式的初始化过程

聚合类
-----------

+ 所有成员都是public的。
+ 没有定义任何的构造函数。
+ 没有类内初始值。
+ 没有基类，也没有virtual函数。

例如，下面的类是一个聚合类：

::

	struct Data{
		int iVal;
		string s;
	}

我们可以提供一个花括号括越来的成员初始值列表，并用它初始化聚合类的数据成员：

::

	// val1.iVal = 0;
	// val1.s = string("Anna");
	Data val1 = { 0, "Anna" };