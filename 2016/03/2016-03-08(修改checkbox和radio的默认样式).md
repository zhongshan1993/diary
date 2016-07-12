# 修改checkbox和radio的默认样式 #

```
.demo1 input[type='radio'], .demo1 input[type="checkbox"]{
    display:none; 
}
label {
    position: relative;
    padding-left: 25px;
    margin-left: 15px;
}
.demo1 label:before{
    content: "";
    display: inline-block;
    width: 17px;
    height: 16px;
    margin-right: 10px;
    position: absolute;
    left: 0;
    bottom: 0;
    background-color: #3797fc;
}
.demo1 input[type='radio'] + label:before{
     border-radius: 8px;
}
.demo1 input[type='checkbox'] + label:before{
     border-radius: 3px;
}
.demo1 input[type='radio']:checked+label:before{
    content: "\2022";
    color: #fff;
    font-size: 30px;
    text-align: center;
    line-height: 19px;
}
.demo1 input[type='checkbox']:checked+label:before{
    content: "\2713";
    font-size: 15px;
    color: #f3f3f3;
    text-align: center;
    line-height: 17px;
}
```