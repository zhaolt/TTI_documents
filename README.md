# TTI Android编码规范

1. 如果一个类不是专门为继承而设计的，那么就应该主动将它加上 **<font color=#f92772>final</font>** 声明，禁止它可以被继承。
2. 源文件编码格式为 **<font color=#ff0000 size=4>UTF-8</font>**。
3. **<font color=#f92772>import</font>**使用**<font color=#ff0000 size=4>自动导包**</font>。
4. 类成员顺序

	>> 类的成员顺序对易学性有很大的影响，但这也不存在唯一的通用法则。不同的类对成员的排序可能是不同的。 
	>> 最重要的一点，每个类应该以某种逻辑去排序它的成员，维护者应该要能解释这种排序逻辑。比如， 新的方法不能总是习惯性地添加到类的结尾，因为这样就是按时间顺序而非某种逻辑来排序的。
	* 区块划分 建议使用注释将源文件分为明显的区块，区块划分如下 
	
		* 常量声明区 
		* UI控件成员变量声明区 
		* 普通成员变量声明区
		* 内部接口声明区
		* 初始化相关方法区 
		* 事件响应方法区 
		* 普通逻辑方法区 
		* 重载的逻辑方法区 
		* 发起异步任务方法区 
		* 异步任务回调方法区
		* 生命周期回调方法区（除去onCreate()方法）
		* 内部类声明区 
	
	* 类成员排列通用规则 
	
		* 按照发生的先后顺序排列 
		* 常量按照使用先后排列 
		* UI控件成员变量按照layout文件中的先后顺序排列 
		* 普通成员变量按照使用的先后顺序排列 
		* 方法基本上都按照调用的先后顺序在各自区块中排列 
		* 相关功能作为小区块放在一起（或者封装掉） 
	
	* 重载：永不分离 
	
		* 当一个类有多个构造函数，或是多个同名方法，这些函数/方法应该按顺序出现在一起，中间不要放进其它函数/方法。 
5. 大括号与 <font color=#f92772>if, else, for, do, while</font>语句一起使用，即使只有一条语句(或是空)，也应该把大括号写上。
	
	```
   if (isSelected()) {
		tv_test.setText("奥利给！");
	} else {
		tv_test.setText("为什么不问问神奇的海螺呢？");
	}
		
	while (calculateResult() != SUCCESSFUL_FLAG) {
		findNextParams();
	}
	```
6. 一行代码不超过<font color=#ff0000 size=5>100</font>个字符，一个方法不超过<font color=#ff0000 size=5>50</font>行，一个类不超过<font color=#ff0000 size=5>2000</font>行（以阅读性为主）。
7. <font color=#f92772>if else</font>嵌套不超过<font color=#ff0000 size=5>3</font>层，<font color=#f92772>for</font>循环不超过<font color=#ff0000 size=5>2</font>层。
8. 不要使用组合声明，比如 ```int a, b;```
9. 控件id命名规范：控件名缩写_控件内容，例如：```iv_back``` (ImageView)。
10. 布局名称命名规范
		
	* ```activity_xxx```
	* ```layout_xxx```(dialog, customer_view, 一般的view)
	* ```item_xxx```(ListView, RecyclerView等列表的item)
	* ```fragment_xxx```
		
11. 资源文件命名规范： 
		
	* 图片：```ic_xxx```(一般图片资源文件)，```bg_xxx```(背景图片资源文件)
	* 颜色：建议非强制：col_数字，按照页面对所有颜色进行分区 
	* 字符串：全局字符串，其余的按照页面区分，较长的用缩写，较短的用全称 
	* shape：```shape_xxx```
	* selector: ```selector_xxx```

12. <font color=#f92772>switch</font>语句：<font color=#f92772>default</font>的情况需要写出来：

	```
	switch(type) {
		    case STEP_ONE:
		        // do something...
		        break;
		    case STEP_TWO:
		        // do something...
		        break;
		    default:
		        // 哪怕什么都不做，也要写上
		        break;
  	}
	```

13. 逻辑性方法需要注释，每个类都需要注释（中文） 
14. 包名全部小写，连续的单词只是简单地连接起来，不使用下划线
15. **<font color=#f92772>public static final</font>** 字段(常量) 全部大写，并用下划线连起来 
	
	```
	public static final String TAG = MainActivity.class.getSimpleName();
	public static final String BASE_URL = "https://www.baidu.com";
	```

16. 方法命名规范

|**方法**|**说明**|
|----|----|
|initXXX()|初始化相关方法，使用init为前缀标识，如初始化布局initView()|
|isXX()checkXX()|方法返回值为<font color=#f92772>boolean</font>型的请使用is或check为前缀标识|
|getXX()|返回某个值的方法，使用get为前缀标识|
|handleXX()|对数据进行处理的方法，尽量使用handle为前缀标识|
|displayXX()/showXX()|弹出提示框和信息，使用display/show为前缀标识|
|saveXX()|与保存数据相关的，使用save为前缀标识|
|resetXX()|对数据重组的，使用reset前缀标识|
|clearXX()|清除数据相关的|
|removeXX()|清除数据相关的|
|drawXX()|绘制数据或效果相关的，使用draw前缀标识|

