# javascript函数绑定 #

函数绑定需要创建一个函数，可以在特定的this环境中以指定参数调用另一个函数。该技巧常常和回调函数与事件处理函数一起使用，以便将函数作为变量传递的同时保留代码执行环境。

首先看下面的例子：

	var handler = {
		message: "event handled",
		handleClick: function (event) {
			alert(this.message);
		}
	}

	var btn = document.getElementById('myButton');
	EventUtil.addHandler(btn, 'click', handler.handleClick); // this对象指向了btn

在上面的例子中，创建了一个叫做handler的对象。`handler.handleClick()`方法被分配为一个DOM的点击事件处理程序。当点击该按钮时，就调用该函数，显示一个警告框。虽然貌似警告框应该显示 "event handled"，但是实际上是"undefined"。这个问题在于没有保存`handler.handleClick()`的环境，所以this对象最后指向了DOM按钮而非handler（在IE8中指向window）。

如下面的例子所示，可以使用闭包来解决问题：

	var handler = {
		message: "event handled",
		handleClick: function (event) {
			alert(this.message);
		}
	}

	var btn = document.getElementById('myButton');
	EventUtil.addHandler(btn, 'click', function(){
		handler.handleClick();
	});

这个解决方案是在onclick事件处理程序内使用了一个闭包直接调用 `handler.handleClick()`。当然，这是特定于这段代码的解决方案。创建多个闭包可能会使代码难于理解和调试，因此，很多javascript库中都实现了一个可以将函数绑定到指定环境的函数。这个函数一般都叫`bind()`。

一个简单的bind函数，接收一个函数和一个环境，并返回一个在给定环境中调用给定函数的函数，并且将所有参数原封不动传递过去。

语法如下：

	function bind(fn, context) {
		return function() {
			fn.apply(context, arguments);
		}
	}


在`bind()`中创建了一个闭包，闭包使用`apply()`调用传入的函数，并给`apply()`传递context对象和参数。这里使用的`arguments`对象是内部函数的，而非`bind()`函数的。当调用返回的函数时，它会在给定环境中执行被传入的函数并给出所有的参数。`bind()`函数按照如下方式调用：

	var handler = {
		message: "event handled",
		handleClick: function (event) {
			alert(this.message);
		}
	}

	var btn = document.getElementById('myButton');
	EventUtil.addHandler(btn, 'click', bind(handler.handleClick, handler));


在这个例子中，我们用`bind()`函数创建了一个保持执行环境的函数，并将其传给`EventUtil.addHandler()`，event对象也被传给了该函数。

如下所示：

	var handler = {
		message: "event handled",
		handleClick: function (event) {
			alert(this.message + ':' + event.type);
		}
	}

	var btn = document.getElementById('myButton');
	EventUtil.addHandler(btn, 'click', bind(handler.handleClick, handler));


`handler.handleClick()`方法和平时一样，获得了event对象，因为所有的参数都通过被绑定的函数传给了它。

ECMAScript5为所有的函数都定义了原生的`bind()`方法，进一步简化了操作。


被绑定函数与普通函数相比有很大的开销，它们需要更多的内存，同时也因为多重函数调用稍微慢一点，所以最好在必要的时候调用。


