---
title: 认识Web和Web标准
publish: false
---

<ArticleTopAd></ArticleTopAd>

### 让flex盒子中的子元素们，居中

flex布局常用的三行代码：

```
    display: flex;
    justify-content: center; // 子元素在横轴的对齐方式 （左右居中）
    align-items: center;  // 子元素在竖轴的对齐方式（上下居中）
```


### 让文字只显示一行，超出显示省略号

```
	overflow: hidden;
	white-space: nowrap;
	text-overflow: ellipsis;

```


### 让文字最多只显示两行，超出后显示省略号

```
	overflow:hidden;
	text-overflow:ellipsis;
	display:-webkit-box;
	-webkit-box-orient:vertical;
	-webkit-line-clamp:2;
```

参考链接：<https://blog.csdn.net/NN_nan/article/details/55045562>



### 问题描述：文本内容里自带了换行，但是在前端没有展示出来

解决办法：增加如下属性即可。

```
white-space: pre-wrap;
```

或者：

```
white-space: pre-line;
```


### 鼠标悬停时，弹出提示文字

参考链接：[css实现鼠标悬浮后的提示效果](https://www.cnblogs.com/zhaojian-08/p/10074660.html)


### 图片的宽度固定，高度自适应

这个场景下，别用background。直接放img元素就好了，将图片的高度设置为`auto`。


### 通过CSS扩大点击热区

```css
.button {
	position: relative;
	/* [其余样式] */
}

.button::before {
	content: '';
	position: absolute;
	top: -10px;
	right: -10px;
	bottom: -10px;
	left: -10px;
}
```
注意，button 里面不要写 `overflow: hidden` 属性，否则扩大的热区无效。

### 2020-10-09-上下滚动，不显示滚动条

```css
.sku_list {
	margin-left: 25rpx;
	display: flex;
	flex-wrap: wrap;

	height: 617rpx;
	overflow: hidden;
	overflow-y: scroll;

	/* 去掉滚动条 */
	&::-webkit-scrollbar {
		display: none;
	}
}
```

注意，去掉滚动条的那行代码里，建议用`display: none;`，不要用`width: 0;`。因为，当你需要设置横向滚动的效果时，`display: none;`这个属性的效果更好，不会改变容器的size；`width: 0;`可能会改变容器的size。


### 设置页面的宽高，撑满屏幕

一般来说，我们在开发一个页面的时候，默认是希望这个页面的宽高能够撑满屏幕的。代码可以这样写：

```css
.app {
	width: 100vw;
	min-height: 100vh;
}

```

### js中插入CSS

代码举例：

```js
new_element = document.createElement("style");
new_element.innerHTML =(".tucao-content p{font-size:18px;}");
document.body.appendChild(new_element);
```
