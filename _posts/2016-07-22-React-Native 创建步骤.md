---
layout: post
title: react-native 笔记2
comments: true
category: React Native
---

#React-Native 创建步骤
1. 进入当前目录
2. react-native init AViewDemo

## JSX ES6

### 
1. flex属性：
> flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。
2. 最外层只能一个View返回。多个view使用内嵌方式


#### [FlexBox布局](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)
CSS布局，基于盒子模型，display，postion float等

1. flexDirection:row|row-reverse|column|column-reverse
> .box {
  flex-direction: row | row-reverse | column | column-reverse;
}
>* **row（默认值）：主轴为水平方向，起点在左端。**
>* row-reverse：主轴为水平方向，起点在右端。
>* column：主轴为垂直方向，起点在上沿。
>* **column-reverse：主轴为垂直方向，起点在下沿。**
![image](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071005.png")

2. justify-content:
![image](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071010.png)

3. alignItems： baseline适用于网页端。默认值为stretch（占满空间）
![image](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071011.png)

4. flex-wrap:默认情况下，项目都排在一条线（又称"轴线"）上
flex-wrap属性定义，如果一条轴线排不下，如何换行。
![image](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071006.png)
> .box{
  flex-wrap: nowrap | wrap | wrap-reverse;
}

5. align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。
6. align-self属性
![image](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071016.png)


#### 获取屏幕分辨率
