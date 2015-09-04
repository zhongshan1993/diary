# javascript中两种继承的方法 #

**组合继承**

组合继承是最常用的继承模式


    <script type="text/javascript">
    	/**
    	 * 
    	 * 最常用的继承模式
    	 */
    	function SuperType(name) {
    		this.name = name;
    		this.color = ['red', 'green', 'blue'];
    	}
    	SuperType.prototype.sayName = function() {
    		alert(this.name);
    	}
    
    
    	function SubType(name, age) {
    		// 继承属性
    		SuperType.call(this, name);
    		this.age = age;
    	}
    	// 继承方法
    	SubType.prototype = new SuperType();
    
    	SubType.prototype.sayAge = function() {
    		alert(this.age);
    	}
    
    	var instance1 = new SubType('zhong', 23);
    	instance1.color.push('black');
    	alert(instance1.color);
    	instance1.sayName();
    	instance1.sayAge();
    
    	var instance2 = new SubType('shan', 12);
    	alert(instance2.color);
    	instance2.sayName();
    	instance2.sayAge();
    </script>


**寄生组合式继承**

开发人员普遍认为寄生组合式模式是引用类型最合适的继承方式


    <script type="text/javascript">
    	/**
    	 * 寄生组合式继承
    	 *
    	 * 借用构造函数来继承属性，通过原型链的混成形式来继承方法
    	 * 不必为了指定子类型的原型而调用超类型的构造函数，所需要的只是超类型原型的一个副本而已
    	 * 
    	 */
    	
    	function object(o) {
    		function F(){};
    		F.prototype = o;
    		return new F();
    	}
    
    	function inheritPrototype(subType, superType) {
    		var prototype = object(superType.prototype); // 创建对象
    		prototype.constructor = subType; // 增强对象
    		subType.prototype = prototype;	// 指定对象
    	}
    
    
    	function SuperType(name) {
    		this.name = name;
    		this.colors = ['red', 'green', 'blue'];
    	}
    	SuperType.prototype.sayName = function() {
    		alert(this.name);
    	}
    	function SubType(name, age) {
    		SuperType.call(this, name);
    		this.age = age;
    	}
    
    
    	inheritPrototype(SubType, superType);
    
    
    	SubType.prototype.sayAge = function() {
    		alert(this.age);
    	}
    	
    </script>