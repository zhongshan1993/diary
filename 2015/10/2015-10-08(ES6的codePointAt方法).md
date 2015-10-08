# ES6的codePointAt方法 #

**ES6加强了对Unicode的支持，并且扩展了字符串对象**

在javascript内部，字符以UTF-16的格式储存，每个字符固定为2个字节。对于那些需要四个字节存储的字符（Unicode编号大于0xFFFF的字符），javascript会认为它们是两个字符。

	var s = "及"; 
	
	s.length //2
	s.charAt(0) // ''
	s.charAt(1) // ''
	s.charCodeAt(0) // 37721
	s.charCodeAt(1) // 65533

上面的代码说明，对于四个字节存储的字符，javascript不能正确处理。字符串的长度被误判为2，而`charAt()`方法无法读取到字符，`charCodeAt()`方法只能分别返回前两个字节和后两个字节的值。

**ES6提供了`codePointAt()`方法**，能够正确处理4个字节存储的字符，返回一个字符的Unicode编号。

`codePointAt()`方法的参数，是字符在字符串中的位置（从0开始）。它会正确的返回四字节UTF-16字符的Unicode编号。对于那些两个字节存储的常规字符，它的返回结果与`charCodeAt`相同。

`codePointAt()`方法是测试一个字符由两个字节还是四个字节组成的最简单的方法。

	function is32Bit(c) {
		return c.codePointAt(0) > 0xFFFF;
	}

