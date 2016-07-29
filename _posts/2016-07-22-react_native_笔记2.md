---
layout: post
title: react-native 笔记2
comments: true
category: React Native
---
# React Native 笔记2

## 1 TextInput
#####  1. 继承自UIView，类似oc中的UITextField
#####   2. 相关属性:
* value字符串型 
* onChangeText函数
* keyboardType键盘类型
> url,default,number-pad
* multiline 布尔型 是否多行 TextView
* password 布尔型 只能一行~~
* clearButtonModel
* onChange 函数
* placeholder
 
  

## 引入外部js，方便iOS和android两端直接调用
//ES5
module.exports = XXXX;
//ES6
export default class MyComponent extends Component{
    ...
}
var XXXX = required('./xxxx.js');

## 适配两端
width和height采用Dimensions方式获取，不可写死

## 组件的生命周期
**实例化** 生存 销毁阶段
![image](../images/live.png)
> componentDidMount 类似oc viewDidLoad，添加网络请求,定时器等
> this.setState 是否render：reactnative有自己的机制判断是否需要刷新对应的组件，无改变就不更新
> 获取真实的DOM节点：通过ref。通过this.refs.xxx获取到
> this.props this.states分别为获取固定属性值，可改变的状态值

### DOM Diff算法
自行谷歌了解

## ES5 ES6差异化
[ES5 ES6写法对照表
](http://reactnative.cn/post/15)

## ScrollView
1. *记住ScrollView必须有一个确定的高度才能正常工作，因为它实际上所做的就是将一系列不确定高度的子组件装进一个确定高度的容器（通过滚动操作）。要给一个ScrollView确定一个高度的话，要么直接给它设置高度（不建议），要么确定所有的父容器都已经绑定了高度。在视图栈的任意一个位置忘记使用{flex:1}都会导致错误，你可以使用元素查看器来查找问题的原因。*
2. *ScrollView内部的其他响应者尚无法阻止ScrollView本身成为响应者。*

> contentContainerStyle:这些样式会应用到一个内层的内容容器上，所有的子视图都会包裹在内容容器内
> horizontal:当此属性为true的时候，所有的的子视图会在水平方向上排成一行，而不是默认的在垂直方向上排成一列。默认值为false。
> keyboardDismissMode:用户拖拽滚动视图的时候，是否要隐藏软键盘。

* none（默认值），拖拽时不隐藏软键盘。

* on-drag 当拖拽开始的时候隐藏软键盘。

* interactive 软键盘伴随拖拽操作同步地消失，并且如果往上滑动会恢复键盘。安卓设备上不支持这个选项，会表现的和none一样。

> keyboardShouldPersistTaps:当此属性为false的时候，在软键盘激活之后，点击焦点文本输入框以外的地方，键盘就会隐藏。如果为true，滚动视图不会响应点击操作，并且键盘不会自动消失。默认值为false。
> onScroll function  在滚动的过程中，每帧最多调用一次此回调函数。调用的频率可以用
> scrollEventThrottle属性来控制。

> refreshControl element 指定RefreshControl组件，用于为ScrollView提供下拉刷新功能。

>removeClippedSubviews bool  实验特性）：当此属性为true时，屏幕之外的子视图（子视图的overflow样式需要设为hidden）会被移除。这个可以提升大列表的滚动性能。默认值为true。

> showsHorizontalScrollIndicator bool 

当此属性为true的时候，显示一个水平方向的滚动条。

> showsVerticalScrollIndicator bool 

当此属性为true的时候，显示一个垂直方向的滚动条。








