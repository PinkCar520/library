### 1. HTML5、CSS3有哪些新特性？
HTML5
**语义化标签：** 如 `<header>`、`<nav>`、`<article>`、`<section>` 更清晰地描述文档结构和内容。
**媒体元素：** `<video>` 和 `<audio>` 标签允许直接在网页上嵌入音频和视频内容
**Canvas 绘图：** `<canvas>` 标签提供了一种绘制 2D 图形的方法，使得动画和图形处理变得更容易。
**本地存储：** 通过 `localStorage` 和 `sessionStorage`，网页可以在本地存储数据。
**表单增强：** HTML5 表单元素引入了新的输入类型（如 `email`、`number`、`date`）和属性（如 `required`、`placeholder`），提升了表单的用户体验。
**地理位置定位：** `Geolocation API` 允许网页获取用户的地理位置信息，用于定位服务和位置感知应用。
**Web Workers：** 允许在后台线程中运行 JavaScript，提高了多线程处理能力。

CSS3:
**选择器增强：** CSS3 引入了更多强大的选择器，如属性选择器、伪类选择器，使得选择和操作元素更加灵活。
**圆角和阴影：** `border-radius` 和 `box-shadow` 属性允许创建圆角和阴影效果，减少了需要使用图片的情况。
**过渡和动画：** `transition` 和 `animation` 属性使得在元素状态改变时实现平滑的过渡和动画效果成为可能。
**多列布局：** `columns` 属性支持多列布局，使得创建多列的文本布局变得更容易。
**媒体查询：** `@media` 查询允许根据设备的特性和屏幕大小来应用不同的样式，实现响应式设计。
**Web 字体：** `@font-face` 允许网页开发者使用自定义字体，不再受限于系统默认字体。
**渐变：** `linear-gradient` 和 `radial-gradient` 属性支持创建平滑渐变效果，取代了过去使用图片实现的效果。
### 2. rem是如何做适配的？
使用 `rem` 进行适配是一种相对于视口的相对单位，它能够根据根元素的字体大小来调整元素的尺寸，从而实现不同设备上的适配。以下是使用 `rem` 进行适配的一般步骤：

1. **设置根元素字体大小：** `在 CSS 中，将根元素通常是 <html> 元素的字体大小设置为一个相对于视口的值，例如 fontSize: 16px 。这将作为基准字体大小，其他元素的尺寸将根据这个值进行调整
2. **使用 rem 单位：**` 在设计和编写 CSS 样式时，使用 `rem` 单位来定义元素的尺寸、边距、内边距等。一个 `rem` 单位等于根元素的字体大小。例如，如果根元素字体大小设置为 `16px`，那么 `1rem` 就等于 `16px`。`
3. **动态调整根元素字体大小：**` 为了实现不同设备的适配，可以使用 JavaScript 监听视口大小变化，然后动态调整根元素的字体大小。这样，当设备的屏幕尺寸改变时，元素的大小会自动调整以适应新的视口大小。`
	`window.addEventListener('resize', function() { 
		`var screenWidth = window.innerWidth; 
		`var baseFontSize = screenWidth / 20; // 1/20 视口宽度作为基准字体大小 document.documentElement.style.fontSize = baseFontSize + 'px'; 
	``});`
### 3. 解决了哪些移动端兼容性的问题？

### 4. 清除浮动的方法有哪些？
	1. 父盒子添加 overflow:hidden
	2. 双伪元素：
	.clearfix::after {
			content: ' ',
			display: 'table',
			clear: both
	}
### 5. 盒子水平垂直居中的方法？
	1. flex布局：父元素的 `display` 属性设置为 `flex`，然后使用 `justify-content` 和 `align-items` 属性来分别控制水平和垂直居中
		display: flex; align-items: center; justify-content: center;
	2. 使用绝对定位和transform: 将要居中的盒子设置为绝对定位，然后使用transform将其位移到中心位置。
		.parent {
			postion: relative;
			.child { 
				position: absolute;
				left: 50%;
				top: 50%;
				transform: translate(-50%,-50%);
		}
	3. 使用绝对定位,利用 margin:auto 属性，对已知宽高的盒子进行自动偏移定位
	4. 表格布局： 将父元素设置为 `display: table;`，然后将子元素设置为 `display: table-cell;`，并使用 `vertical-align` 控制垂直居中。
	.parent { 
		display: table; 
		.child { 
			display: table-cell; 
			text-align: center; /* 水平居中 */ 
			vertical-align: middle; /* 垂直居中 */ 
		}
	}