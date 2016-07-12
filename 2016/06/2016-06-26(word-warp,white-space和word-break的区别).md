# word-warp,white-space和word-break的区别 #

一直弄不清这三者的区别和联系，属性和值都特别绕，也不好记……

1. word-wrap: break-word; 内容将在边界内换行，仅应用于块级元素，内联元素要用的话，必须要设定width, height或display: block或position: absolute。
2. word-break: break-all; 用于处理单词折断。
3. white-space:nowrap; 用于处理元素内的空白，只在一行内显示。