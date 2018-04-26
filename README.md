# font-end-interview
font-end-interview-QA

1、前端如何自动传cookie:

    非跨域下：
	在HTTP Request请求头加上 Cookie: header 发送给浏览器；

	跨域下：
	在前端请求头上加上：widthCredentials: true
    在服务器端设置：Access-Control-Allow-Credentials：true
                    Access-Control-Allow-Origin: 特定域名不能为*

2、JS为什么是单线程运行的：(JS运行机制)

    作为浏览器的脚本语言，Javascript的主要用途是与用户互动，以及操作dom，
    这就决定了它只能是单线程的，否则会带来复杂的同步问题。例如：多线程同时
    修改dom就会造成混乱。

    => 任务队列 => 同步任务和异步任务 => EventLoop（事件循环）

3、谈谈你对跨域的理解


JS方面:

1、let与var的区别：

    if (!('a' in window)) {
        var a = 1;   
    }
    alert (a); // undefined
    var存在变量提升，所以'a' in window 为true，即a没有进行赋值，输出为undefined
    if (!('a' in window)) {
        let a = 1;   
    }
    alert (a); // 报错
    区别：let不存在变量提升、暂时性死区、不允许重复声明


2、数组的内置方法有哪些:
    
	push()      // 添加元素
	pop()       // 删除数组尾部最后一个元素
	shift()     // 删除数组头部第一一个元素
	unshift()   // 向数组头部添加一个或多个元素
	slice()     // 截取数组部分的长度，返回新的数组
	concat()    // 数组合并返回新的数组，原数组没有改变
	indexOf()   // 搜索指定元素的索引位置
	splice()    // 从指定的索引开始向数组添加或删除元素
	sort()      // 给数组重新排序
	join()      // 将数组用指定字符串连接起来
	reverse()   // 数组倒序

    ES6:
    copyWithin() // 在数组内部将制定位置的成员复制到其他位置，会覆盖原来的成员
    find()       // 找出第一个符合条件的数组成员
    findIndex()  // 找出第一个符合条件的数组成员的索引
    fill()       // 使用给定值填充数组
    includes()   // 判断数组是否包含指定值
    
    entries()    // 遍历数据，返回[index, value]形式为数组成员的数组
    keys()       // 遍历数据，返回index形式为数组成员的数组
    values() 	// 遍历数据，返回value形式为数组成员的数组
    map()        // 遍历数据，返回新数组
    
    遍历：
    forEach()    // 返回所有数组成员
    filter()     // 返回符合条件的数据成员，形成新数组
    every()      // 所有数组成员满足条件返回true, 否则为false
    some()       // 有一个数组成员满足条件返回true
    
    数组拷贝的几种方法：
    A、浅拷贝
    arrN = arr
 
    B、简单深拷贝(单层)
    使用slice和concat内置方法：
    var arrN = arr.slice(0);
    --------------------------
    var arrN = [];
    arrN.concat(arr);
 
    使用map返回新数组 // var arrN = arr.map(value => value)
    使用filter返回新数组 // var arrN = arr.filter(() => true)
 
    C、深拷贝(多层)
    var deepCopy = function (o) {
    	if (o instanceof Array) {
    		var n = [];
	        for (var i = 0, len = o.length; i < len; i++) {
				n[i] = deepCopy(o[i]);
	        }
	        return n;
    	} else if (o instanceof Object) {
    		var n = {};
			for (var key in o) {
				n[key] = deepCopy(o[key]);
			}
			return n;
    	} else {
    		return o;
    	}
    }

3、对象的内置方法有哪些：


4、window.onload与ready的区别

	ready：表示文档结构已经加载完成（不包括图片等非文字媒体文件）
	onload：表示页面包含图片等文件在内的所有元素都加载完成

	ready在onload前加载

	document.ready => $(function() { // do something }) => $(document).ready(function () {});
	window.onload => $(window).load(function () {})

CSS方面：

1、伪类和伪元素的区别
	
	CSS 伪类用于向某些选择器添加特殊的效果。
    CSS 伪元素用于将特殊的效果添加到某些选择器。

    伪类种类：
    :active
    :focus
    :hover
    :link
    :visited
    :first-child
    :lang // 允许创作者来定义指定的元素中使用的语言

    伪元素种类：
    :first-letter // 将特殊样式添加到文本的首字母
    :first-line   // 将特殊样式添加到文本的首行
    :before
    :after

    伪类的效果可以通过添加一个实际的类来达到，而伪元素的效果则需要添加一个实际的元素才能达到，
    这就是为什么他们一个成为伪类，一个称为伪元素的原因

    CSS3规定伪类使用一个冒号表示，伪元素使用两个冒号来表示，即：
    :Pseudo-classes
    ::Pseudo-elements

2、选择器及其权重排序
	
	id选择器(#div)

	类选择器(.div)
	属性选择器(rel[....])
 	伪类选择器(:hover)

	相邻选择器(div + p)
	子选择器(div > p)
	后代选择器(div p)
	标签选择器(p)
	伪元素选择器(:before)

	通配符选择器(*)

 	权重规则：
 	!important > 内联样式 > id选择器 > 类选择器 > 类型选择器 > 继承 > 通配符
 	           > 1000     > 100      > 10       > 1



库/框架方面：

1、谈谈你对双向绑定的理解

工程化方面：

1、git-flow的认识


