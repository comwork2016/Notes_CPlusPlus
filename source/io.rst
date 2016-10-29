.. _io:

IO库
===========

IO类
^^^^^^^^

- iostream:定义用于读写流的基本类型

	istream,ostream,iostream

- fstream:定义读写命名文件的类型

	ifstream,ofstream,fstream

- sstream:定义读写内存string对象的类型

	istringstream,ostringstream,stringstream

IO对象无拷贝或赋值
---------------------

::

	ofstream out1,out2;
	out1 = out2;				// 错误：不能对流对象赋值
	ofstream print(ofstream);	// 错误：不能初始化ofstream参数
	out1 = print(out2);			// 错误：不能拷贝流对象

管理输出缓冲
--------------

- 程序正常结束
- 缓冲区满时
- 可以使用操纵符如endl来显示刷新缓冲区
	
::

	cout<<"hi!"<<endl; 	// 输出hi和一个换行，然后刷新缓冲区
	cout<<"hi!"<<flush;	// 输出hi，然后刷新缓冲区，不附加任何额外字符
	cout<<"hi!"<<ends;	// 输出hi和一个空字符，然后刷新缓冲区

- 每个输出操作之后，可以用操纵符unitbuf设置流的内部状态，来清空缓冲区

::
	
	cout<<unitbuf;		// 所有输出操作后都会立即刷新缓冲区
	// 任何输出都会立即刷新，无缓冲
	cout<<nounitbuf;	//回到整张的缓冲方式
	
- 一个输出流可能被关联到另一个流

	cin >> ival; 会导致cout的缓冲区被刷新