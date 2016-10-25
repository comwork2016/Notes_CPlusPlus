.. _variable_type:

变量和基本类型
=================

复合类型
---------

- 指针是对象面引用不是。
- 定义引用时，程序把引用和它的初始值绑定在一起，一旦初始化完成，引用将和它的初始值一直绑定在一起，无法再将引用重新绑定到另外一个对象。

const限定符 
----------------

- 默认状态下，const对象仅在文件内有效，如果需要在多个文件中都能访问到const的初始值，就必须在多个文件中声明const对象（用到 **extern** ）。
- 下面的代码会将ri绑定到一个int类型的临时变量上，c plus plus primer上面说是非法的，但是在g++ c++11上可以运行。

::

	double dVal = 3.14;
	const int& ri = dVal;

- 将*放在const指针之前用以说明指针是一个常量（顶层const），不能被改变。

- 常量表达式constexpr  

	+ const int limits = 20; //limits是一个常量表达式
	+ const int sz = getSize(); //sz不是一个常量表达式，因为sz的值只有在运行时才能得到
	+ constexpr必须用常量表达式来初始化，const int sz = getSize();只有在getSize()是一个常量表达式时才不战正确
	+ 在constexpr声明中如果定义了一个指针，限定符constexpr仅对指针有效，与指针所指的对象无关