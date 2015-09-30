 # ECMAScript中的let #

**自从开始接触前端的这两年时间里，总是或多或少地听人说ES6，自己的基础不够，所以总时告诫自己要先去学习基础的东西。直到这几天，才开始研究ES6，看的是[阮一峰](http://www.ruanyifeng.com/home.html)的ECMAScript6入门。**


下面的代码如果使用的var,则最后输出的是“9”

	var a = [];
	for (var i = 0; i < 10; i++) {
		var c = i;
		a[i] = function() {
			console.log(c);
		};
	}
	a[6]();// 9


而如果使用let,声明的变量仅仅在块级作用域内有效,于是最后输出的是“6”


	var a = [];
	for (var i = 0; i < 10; i++) {
		let c = i;
		a[i] = function() {
			console.log(c);
		};
	}
	a[6]();// 6