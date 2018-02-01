---
layout: post
title:  "Reactjs 中表单数据绑定value后不可编辑问题？"
date:   2018-01-15 15:15:26 +0800
author: "孙印凤"
categories: sunyinfeng
---

### Reactjs 中表单数据绑定value后不可编辑

初次使用React，在处理input组件时需要对用户输入数据进行校验，选择在state改变时进行校验。例如手机号的校验是在用户输入失去焦点时进行校验，给input定义了onBlur事件。

{% highlight ruby %}
<Input name="出生日期" id="birthday" type="date" change={this.changeFun} value={this.state.birthday}/>
{% endhighlight %}
但是当添加value绑定后，该input就不可编辑了！

后来查找资料发现，在React中数据流是单向的，针对表单元素，需要使用
**onChange** 事件进行监听。

{% highlight ruby %}
<input onChange={(e) => this.inputPara(e.target.name, e.target.value)} />
{% endhighlight %}
这样之后就会出现一个问题：需要校验的输入框输入值一直有问题，其实问题出在：++不应该在用户输入改变state值进行校验，而是应该在提交操作再去检验++！！
> 在用户提交时再去检验相应字段的state值。