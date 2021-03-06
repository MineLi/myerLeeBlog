---
title: markdown .md 语法
date: 2017-04-20 13:57:40
tags: markdown
keywords: markdown 语法 
---
 # 1.标题
---------
在文本下面加上 `=` ，那么上方的文本就变成了大标题。在文本下面加上 `-` ，那么上方的文本就变成了中标题，显示出来比大标题小点。`=` 和 `-`的个数无限制，至少一个。

除此以外，关于标题还有等级表示法，分为六个等级，显示的文本大小依次减小。不同等级之间是以井号  `#`  的个数来标识的。一级标题有一个 `#`，二级标题有两个`#` ，以此类推。
<!-- more --> 
```
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```

其实，大标题和中标题是分别和一级标题和二级标题对应的。即大标题大小和一级标题相同，中标题大小和二级标题相同。

# 2.普通文本
---------------
直接输入的文字就是普通文本。需要注意的是要换行的时候不能直接通过回车来换行，需要使用 `<br>` (或者`<br/>`)。也就是html里面的标签。事实上，md的语法里支持大部分的html语法。


	<br/> 前需要加反斜杠 \ ，目的就是像其他语言那样实现转义
# 3.单行文本
---------------
在普通文本每一行前加两个 tab 符 就可以实现单行文本的显示

	第一行
    第二行
    第三行
# 4.部分文字的高亮
---------------

如果你想使一段话中部分文字高亮显示，来起到突出强调的作用，那么可以把它用 \`  \` 包围起来。注意这不是单引号，而是左上角esc下的~键 注意是英文输入法下。  `这是高亮效果`

# 5.文字超链接
---------------

即在URL之后 用双引号括起来一个字符串。同样要注意这里是英文双引号。

		语法：1.[我的博客](http://limingyang.xyz);
              2.直接写超链接 http://limingyang.xyz
显示效果分别为：
	
[我的博客](http://limingyang.xyz);

http://limingyang.xyz

# 6.插入符号
<!------------------->

## 无序列表
语法是在没一个list前加一个 `*` ,注意`*`后面要有一个空格，效果是：

* 第一列
* 第二列
* 第三列

## 多级的无序列表 
在无序列表基础上 第二行加一个Tab，第三行加两个Tab。这样用来表示层级结构就很清晰了
* 第一列
	* 第二列
		* 第三列

# 7.插入图片
---------------
 ## 插入网络上的图片
 最简单的 ：`![图片没找到显示的文字](http://www.baidu.com/img/bdlogo.gif)` 
 
![图片没找到显示的文字](http://www.baidu.com/img/bdlogo.gif)

## 插入本地图片
### 相对路径

比如:你把一个叫做1.png的图片和*.md文件放在一起，那么你就可以用这种方式插入图片`![](a.png)`

### 绝对路径

如Windows中写  D:\a.png (相当不推荐)

### 将文件base 64 转码

  http://tool.css-js.com/base64.html 生成编码后的代码 `data:image/jpg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2w ... `
  
 将生成的编码 放入（）内 `![](data:image/jpg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2w ...)`
 这洋生成的编码会很长，影响美观 也可以用变量`![](imgdata)` 然后在文章末尾 `imgdata：data:image/jpg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2w ... `
 
### 上传到云空间
 [七牛](https://www.qiniu.com/)、[MPic上传工具](http://mpic.lzhaofu.cn/) 一键生成链接引入
 `![](http://oopl89lfl.bkt.clouddn.com/myerlee/20170421/203237869.jpg)`
 

# 8.插入代码片段
---------------
我们需要在代码的上一行和下一行用 \`\`\` 标记。\`\`\` 不是三个单引号，而是数字1左边，Tab键上面的键。要实现语法高亮那么只要在  \`\`\` 之后加上你的编程语言即可（忽略大小写）

	```javascript
		function(){
			console.log("111");
		}
	```
显示效果如下：
```javascript
function(){
	console.log("111");
}
```
# 9.插入表格
---------------

	| 排序方法 | 平均情况 | 最好情况 | 最坏情况 | 辅助空间 | 稳定性 |
	|:-----|:-----|:-----|:-----|:-----|:-----|
	| 冒泡排序 | O(n²) | O(nlogn) | O(n²) | O(1) | 稳定 |
	| 简单选择 | O(n²) | O(n²) | O(n²) | O(1) | 稳定 |
	| 直接插入 | O(n²) | O(n) | O(n²) | O(1) | 稳定 |
	| 希尔排序 | O(nlogn)~O(n²) | O(n^1.3) | O(n²) | O(1) | 不稳定 |
	| 堆排序 | O(nlogn) | O(nlogn) | O(nlogn) | O(1) | 不稳定 |
	| 归并排序 | O(nlogn) | O(nlogn) | O(nlogn) | O(n) | 不稳定 |
	| 快速排序 | O(nlogn) | O(nlogn) | O(n²) | O(nlogn)~O(n) | 不稳定 |

第一行：第一行要显示的，类似Thead
第二行：对齐方式|:-----|左对齐，|:-----:|居中，|-----:|右对齐
每列的宽度是根据对应列里最长的文本来决定

另外：代码高亮功能是引入了 highlightjs 插件 在 head 里面插入这三行代码即可
```html
	<link rel="stylesheet" href="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.11.0/styles/default.min.css">
	<script src="//cdnjs.cloudflare.com/ajax/libs/highlight.js/9.11.0/highlight.min.js"></script>
	<script>hljs.initHighlightingOnLoad();</script>
```




 
 
 
 




