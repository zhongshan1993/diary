# Android应用TextView实现跑马灯效果 # 

**接近两个月的时间，因为生病回家，在家不方便学习等等原因，技术日志终止了大约一个多月，今天是2月2号，转眼已经是2016年了，2016对我又是一个人生的转折点——面对第一份工作。今年可能会改变很多，或者离别很多。无论怎样，保持学习的状态总不会错的，加油！**



- layout

    <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:tools="http://schemas.android.com/tools"
        android:layout_width="fill_parent"
        android:layout_height="fill_parent"
        android:orientation="horizontal" >

        <com.example.marqueetextviewdemo.MarqueeText
            android:id="@+id/textView1"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="@string/hello_world" 
            android:singleLine="true"
            android:ellipsize="marquee"
            android:focusable="true"
            android:focusableInTouchMode="true" />
        
        <com.example.marqueetextviewdemo.MarqueeText
            android:id="@+id/textView2"
            android:layout_below="@+id/textView1"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:text="@string/hello_world" 
            android:singleLine="true"
            android:ellipsize="marquee"
            android:focusable="true"
            android:focusableInTouchMode="true" />

    </RelativeLayout>


- class

    package com.example.marqueetextviewdemo;

    import android.content.Context;
    import android.util.AttributeSet;
    import android.widget.TextView;

    public class MarqueeText extends TextView {

        public MarqueeText(Context context) {
            super(context);
            // TODO Auto-generated constructor stub
        }

        public MarqueeText(Context context, AttributeSet attrs, int defStyle) {
            super(context, attrs, defStyle);
            // TODO Auto-generated constructor stub
        }

        public MarqueeText(Context context, AttributeSet attrs) {
            super(context, attrs);
            // TODO Auto-generated constructor stub
        }

        @Override
        public boolean isFocused() {
            // TODO Auto-generated method stub
            return true;
        }

    }