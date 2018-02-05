---
layout: post
title:  "border-radius 详解"
date:   2018-02-05 20:14:19 +0800
author: "孙印凤"
categories: sunyinfeng
---
### 语法
{% highlight ruby %}
    border-radius ： none | <length>{1,4} [/ <length>{1,4} ]?
{% endhighlight %}

### 取值
    <length>： 由浮点数字和单位标识符组成的长度值。不可为负值。

### 说明

border-radius是一种缩写方法。如果“/”前后的值都存在，那么“/”前面的值设置其水平半径，“/”后面值设置其垂直半径。如果没有“/”，则水平和垂直半径相等。另外其四个值是按照top-left、top-right、bottom-right、bottom-left的顺序来设置的其主要会有下面几种情形出现：

1、border-radius: [ <length>{1,4} ]; //这里只有一个值，那么top-left、top-right、bottom-right、bottom-left四个值相等

2、border-radius:[ <length>{1,4} ]  [ <length>{1,4} ] ; //这里设置两个值，那么top-left等于bottom-right，并且取第一个值；top-right等于bottom-left，并且取第二个值

3、border-radius:[ <length>{1,4} ]   [ <length>{1,4} ]   [ <length>{1,4} ];//如果有三个值，其中第一个值是设置top-left;而第二个值是top-right和bottom-left并且他们会相等,第三个值是设置bottom-right

4、border-radius:[ <length>{1,4} ]   [ <length>{1,4} ]  [ <length>{1,4} ]   [ <length>{1,4} ];//如果有四个值，其中第一个值是设置top-left;而第二个值是top-right,第三个值bottom-right,第四个值是设置bottom-left

前面，我们主要看了border-radius的缩写格式，其实border-radius和border属性一样，还可以把各个角单独拆分出来，也就是以下四种写法，这里我规纳一点，他们都是先Y轴在X轴，具体看下面：
{% highlight ruby %}
    border-top-left-radius: <length>  <length>   //左上角
    border-top-right-radius: <length>  <length>  //右上角
    border-bottom-right-radius:<length>  <length>  //右下角
    border-bottom-left-radius:<length>  <length>   //左下角
{% endhighlight %}

5、浏览器兼容性
Firefox4.0+、Safari5.0+、Google Chrome 10.0+、Opera 10.5+、IE9+支持border-radius标准语法格式，其他老板浏览器需要做兼容性处理。

6、例子
{% highlight ruby %}
    .demo {
      border-radius: 10px 15px 20px 30px / 20px 30px 10px 15px;
    }
{% endhighlight %}
等价于
{% highlight ruby %}
    .demo {
      border-top-left-radius: 10px 20px;
      border-top-right-radius: 15px 30px;
      border-bottom-right-radius: 20px 10px;
      border-bottom-left-radius: 30px 15px;
    }
{% endhighlight %}

![效果如图所示](/assets/img/br1.png)

{% highlight ruby %}
    .demo {
      border-radius: 10px / 20px;
    }

{% endhighlight %}
等价于
{% highlight ruby %}
    .demo {
      border-top-left-radius: 10px 20px;
      border-top-right-radius: 10px 20px;
      border-bottom-right-radius: 10px 20px;
      border-bottom-left-radius: 10px 20px;
    }
{% endhighlight %}

![效果如图所示](/assets/img/br2.png)

半圆示例：
{% highlight ruby %}
 #box {
    width:200px;
    height:100px;
    border-radius:100px 100px 0 0;
    background-color:red;
}
{% endhighlight %}

![效果如图所示](/assets/img/br3.png)

#### 参考资料
1. [https://www.w3cplus.com/css3/border-radius](https://www.w3cplus.com/css3/border-radius)
