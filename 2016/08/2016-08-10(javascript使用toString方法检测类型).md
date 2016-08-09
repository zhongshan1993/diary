# javascript使用toString方法检测类型 #

初到公司，一味学习新框架，追求新技术，其实最重要的，还是要把语言的本质弄清楚，才有能力快速掌握新技术...

以下为3个类型检测函数，由于在任何值上调用Object原生的toString()方法，都会返回一个[object NativeConstructorName]格式的字符串。

    function isArray(value) {
        return Object.prototype.toString.call(value) == "[object Array]";
    }

    function isFunction(value) {
        return Object.prototype.toString.call(value) == "[object Function]";
    }

    function isRegExp(value) {
        return Object.prototype.toString.call(value) == "[object RegExp]";
    }
