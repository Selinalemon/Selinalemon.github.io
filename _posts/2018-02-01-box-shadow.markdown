---
layout: post
title:  "探索 CSS3 中的 box-shadow 属性"
date:   2018-02-01 16:56:19 +0800
author: "孙印凤"
categories: sunyinfeng
---
### box-shadow 属性

box-shadow属性是一个CSS3属性，允许我们在几乎任何元素上来创建阴影效果。

1、语法

box-shadow属性接收一个由5个部分组成的值：
{% highlight ruby %}
    box-shadow: offset-x offset-y blur spread color position;
{% endhighlight %}

box-shadow 属性不可拆分且其值是独立的，所以属性值的书写顺序很重要，特别是长度值。

2、offset-x

第一个长度值指定了阴影的水平偏移量。即在x轴上阴影的位置。正值使阴影出现在元素的右边，而负值使阴影出现在元素的左边。
{% highlight ruby %}
    .left { box-shadow: 20px 0px 10px 0px rgba(0,0,0,0.5) }

    .right { box-shadow: -20px 0px 10px 0px rgba(0,0,0,0.5) }
{% endhighlight %}

![效果如图所示](/assets/img/box1.jpg)

3、offset-y

第二个长度值指定了阴影的垂直偏移量。即在y轴上阴影的位置。正值时，其阴影在对象的底部，反之其值为负值时，阴影在对象的顶部；
{% highlight ruby %}
    .left { box-shadow: 0px 20px 10px 0px rgba(0,0,0,0.5) }

    .right { box-shadow: 0px -20px 10px 0px rgba(0,0,0,0.5) }
{% endhighlight %}

![效果如图所示](/assets/img/box2.jpg)

4、blur

第三个长度值代表阴影的模糊半径，此参数是可选，但其值只能是为正值，如果其值为0时，表示阴影不具有模糊效果，其值越大阴影的边缘就越模糊；
{% highlight ruby %}
    .left { box-shadow: 0px 0px 0px 0px rgba(0,0,0,0.5) }

    .middle { box-shadow: 0px 0px 20px 0px rgba(0,0,0,0.5) }

    .right { box-shadow: 0px 0px 50px 0px rgba(0,0,0,0.5) }
{% endhighlight %}

![效果如图所示](/assets/img/box3.jpg)

5、spread

第四个是最后一个长度值，代表着阴影的尺寸。这个值可以被想象成从元素到阴影的距离。正值会在元素的各个方向按指定的数值延伸阴影。负值会使阴影收缩得比元素本身尺寸还小。默认值0会让阴影伸展得和元素的大小一样。
{% highlight ruby %}
    .left { box-shadow: 0px 0px 20px 0px rgba(0,0,0,0.5) }

    .middle { box-shadow: 0px 0px 20px 20px rgba(0,0,0,0.5) }

    .right { box-shadow: 0px 50px 20px -20px rgba(0,0,0,0.5) }
{% endhighlight %}

![效果如图所示](/assets/img/box4.jpg)

6、color

颜色值是阴影的颜色，可以是任何颜色单位。
{% highlight ruby %}
    .left { box-shadow: 0px 0px 20px 10px #67b3dd }

    .right { box-shadow: 0px 0px 20px 10px rgba(0,0,0,0.5) }
{% endhighlight %}

![效果如图所示](/assets/img/box5.jpg)

7、position

box-shadow属性的最后一个值是一个可选的关键字，它代表着阴影的位置。默认情况下，这个值并而没有给出，这意味着阴影是一个外部阴影。我们能通过关键字inset使阴影变成内部阴影。
{% highlight ruby %}
    .left { box-shadow: 20px 20px 10px 0px rgba(0,0,0,0.5) inset }

    .right { box-shadow: 20px 20px 10px 0px rgba(0,0,0,0.5) }
{% endhighlight %}

![效果如图所示](/assets/img/box6.jpg)

8、多重阴影

box-shadow 属性能在单个元素上接受多个阴影。每个阴影通过用逗号分隔的 box-shadow 属性列表来加载。
{% highlight ruby %}
    .foo {
        box-shadow: 20px 20px 10px 0px rgba(0,0,0,0.5) inset, /* inner shadow */
                    20px 20px 10px 0px rgba(0,0,0,0.5); /* outer shadow */
    }
{% endhighlight %}

![效果如图所示](/assets/img/box7.jpg)

9、圆形阴影

box-shadow 属性的边界半径是通过该元素的 border-radius 属性来控制的。
{% highlight ruby %}
    .foo {
        box-shadow: 20px 20px 10px 0px rgba(0,0,0,0.5);
        border-radius: 50%;
    }
{% endhighlight %}

![效果如图所示](/assets/img/box8.jpg)

### 高级的使用方法

1、一种非布局模块边界的替代品

我们可以使用box-shadow属性来创建一种元素，这种元素是边界环绕的，但是它不干扰盒子模型或者页面上面的其他布局。更有甚者，用它来创造出多个阴影，我们可以在元素不同的边上拥有不同样式的边界。
{% highlight ruby %}
    .simple {
        box-shadow: 0px 0px 0px 40px indianred;
    }

    .multiple {
        box-shadow: 20px 20px 0px 20px lightcoral,
                    -20px -20px 0px 20px mediumvioletred,
                    0px 0px 0px 40px rgb(200,200,200);
    }
{% endhighlight %}

![效果如图所示](/assets/img/box9.jpg)

2、弹出效果

在box-shadow（和transform）属性上进行变形，我们能创造出一个元素靠近或者远离使用者的假象。
{% highlight ruby %}
    .popup {
        transform: scale(1);
        box-shadow: 0px 0px 10px 5px rgba(0, 0, 0, 0.3);
        transition: box-shadow 0.5s, transform 0.5s;
    }
    .popup:hover {
        transform: scale(1.3);
        box-shadow: 0px 0px 50px 10px rgba(0, 0, 0, 0.3);
        transition: box-shadow 0.5s, transform 0.5s;
    }
{% endhighlight %}

![效果如图所示](/assets/img/box10.gif)

3、浮动效果

我们能在:after这样的伪元素上增加box-shadow的效果。我们能使用这个来创建出元素底部的阴影，给予元素浮起或者掉落下来的假象。
{% highlight ruby %}
    .floating {
        position: relative;

        transform: translateY(0);
        transition: transform 1s;
    }
    .floating:after {
        content: "";
        display: block;
        position: absolute;
        bottom: -30px;
        left: 50%;
        height: 8px;
        width: 100%;
        box-shadow: 0px 0px 15px 0px rgba(0, 0, 0, 0.4);
        border-radius: 50%;
        background-color: rgba(0, 0, 0, 0.2);

        transform: translate(-50%, 0);
        transition: transform 1s;
    }

    /* Hover States */
    .floating:hover {
        transform: translateY(-40px);
        transition: transform 1s;
    }
    .floating:hover:after {
        transform: translate(-50%, 40px) scale(0.75);
        transition: transform 1s;
    }
{% endhighlight %}

![效果如图所示](/assets/img/box11.gif)

我们能通过box-shadow属性达成许多其他的特效。举个例子，[this popular pen](https://codepen.io/haibnu/pen/FxGsI) 使用这个属性创造出8种类似纸张的效果。即使表面上看起来它是一个用于创建简单阴影的工具，实际上它可远比那个功能强大的多。
