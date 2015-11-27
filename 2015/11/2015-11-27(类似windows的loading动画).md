# 类似windows的loading动画 #

(点这里查看DEMO)[http://zhongshan1993.github.io/myDemo/css3Loading/03.html]
```

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style type="text/css">
        body {
            font-size: 14px;
            margin-top: 100px;
            color: darkgoldenrod;
            text-align: center;
            font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
        }
        span {
            display: block;
            margin: 0 auto;
        }
        span[class*='span1_'] {
            width: 6px;
            height: 6px;
            background-color: #3b68d0;
            display: inline-block;
            margin: 12px 2px;
            border-radius: 50%;
            -webkit-animation: load 4s infinite;
            -moz-animation: load 4s infinite;
            -ms-animation: load 4s infinite;
            animation: load 4s infinite;
        }
        @keyframes load {
            0% {
                transform: translateX(-30px);
                opacity: 0;
            }
            25% {
                opacity: 1;
            }
            50% {
                transform: translateX(30px);
                opacity: 0;
            }
            100% {
                opacity: 0;
            }
        }
        @-webkit-keyframes load {
            0% {
                -webkit-transform: translateX(-30px);
                opacity: 0;
            }
            25% {
                opacity: 1;
            }
            50% {
                -webkit-transform: translateX(30px);
                opacity: 0;
            }
            100% {
                opacity: 0;
            }
        }
        @-moz-keyframes load {
            0% {
                -moz-transform: translateX(-30px);
                opacity: 0;
            }
            25% {
                opacity: 1;
            }
            50% {
                -moz-transform: translateX(30px);
                opacity: 0;
            }
            100% {
                opacity: 0;
            }
        }
        span.span1_1 {
            animation-delay: 1s;
            -webkit-animation-delay: 1s;
            -moz-animation-delay: 1s;
        }
        span.span1_2 {
            animation-delay: .8s;
            -webkit-animation-delay: .8s;
            -moz-animation-delay: .8s;
        }
        span.span1_3 {
            animation-delay: .6s;
            -webkit-animation-delay: .6s;
            -moz-animation-delay: .6s;
        }
        span.span1_4 {
            animation-delay: .4s;
            -webkit-animation-delay: .4s;
            -moz-animation-delay: .4s;
        }
        span.span1_5 {
            animation-delay: .2s;
            -webkit-animation-delay: .2s;
            -moz-animation-delay: .2s;
        }
        span.span1_6 {
            animation-delay: 0s;
            -webkit-animation-delay: 0s;
            -moz-animation-delay: 0s;
        }
    </style>
</head>
<body>
    <div class="wrap">
        <span class="load">Loading</span>
        <span class="span1_1"></span>
        <span class="span1_2"></span>
        <span class="span1_3"></span>
        <span class="span1_4"></span>
        <span class="span1_5"></span>
        <span class="span1_6"></span>
    </div>
</body>
</html>

``` 