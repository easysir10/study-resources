---
MarkDown语法及其Typora快捷键.
---

[TOC]



# MarkDown

## 块元素

### 标题

标题级别1~6，使用 `#+[空格]` 或 快捷键 `ctrl+[数字]`：

```markdown
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```

### 引用文字

在行头输入> 进行块引用 `或` 快捷键`ctrl+shift+Q`：

```markdown
>引用文字。
```

### 列表

#### 有序列表和无序列表

无序列表输入`- [空格]`或`+ [空格]`或`* [空格]`,快捷键`ctrl+shift+]`

有序列表输入`1.[空格]`,快捷键`ctrl+shift+[`

```markdown
- 无序列表
  - 无序列表
    - 无序列表

1. 有序列表
   1. 有序列表

- [ ] 未完成的任务列表
- [x] 完成的任务列表
```

- 无序列表
  - 无序列表
    - 无序列表

1. 有序列表
   1. 有序列表

- [ ] 未完成的任务列表
- [x] 完成的任务列表

#### 任务列表

输入`- [ ]` 或`[x]`创建（未完成或完成）的项目的列表。

```markdown
- [ ] 未完成的任务列表
- [x] 完成的任务列表
```

### 代码块

输入**````[语言]`**创建代码块，快捷键`ctrl+shift+K`

```markdown
​```c
	include<stdio.h>
		int main() {
			print('hello world!');
			return 0;
		}
​```
```

```c
include<stdio.h>
int main() {
	print('hello world!');
	return 0;
}
```

### 数学公式块

`$$ [回车]`创建数学公式代码块，快捷键`ctrl+shift+M`.

**MathJax** 渲染 *LaTeX* 数学表达式

### 表格

输入`| first | second |`创建包含两列的表格，快捷键`ctrl+T`.

```markdown
| first | second|
|-------|-------|
| cell | cell |
```

### 角注

输入[^footnate] `[^footnate]`创建角注.

[^footnate]: This is footnate.

### 水平线

输入`---`或`***`将绘制一条水平线.

### 目录

输入`[toc]+回车`将创建一个‘目录’部分，自动更新.

### 图表 (Sequence, Flowchart and Mermaid)

Typora 支持, [sequence](https://bramp.github.io/js-sequence-diagrams/), [flowchart](http://flowchart.js.org/) and [mermaid](https://knsv.github.io/mermaid/#mermaid), 使用前要先从偏好设置面板启用该功能。

详细信息请参阅此 [文档](http://support.typora.io/Draw-Diagrams-With-Markdown/) 

```flow
st=>start: 开始
op=>operation: My Operation
cond=>condition: Yes or No?
e=>end
st->op->cond
cond(yes)->e
cond(no)->op
```

## Span元素

### 链接

链接语法`[name](link)`，快捷键`Ctrl+K`,按住ctrl点击跳转.

#### 内链接

内链接语法`[](#元素块)`.

[代码块在这里](#代码块)

#### 参考链接

参考链接语法`[name][id]`,[name][id]

[id]: https://www.baidu.com

#### URL网址

语法`<url>`

### 图片

添加图片语法`![替代文字](url)`,快捷键`ctrl+shift+I`.

## 文本样式

### 斜体

语法`_[文本]_`或`*[文本]*`，*快捷键*`ctrl+I`.

### 粗体

语法`**[文本]**`或`__[文本]__`,快捷键 **ctrl+B**

### 代码

语法\`[文本]\` 

### 删除线

删除线`~~[文本]~~`，~~快捷键~~ **alt+shift+5**

### 下划线

下划线`<u>[文本]</u>`,<u>快捷键</u> <u>ctrl+U</u>

### 表情符号:smile:

微笑表情`:smile:`

### 下标

下标`H~2~O`，H~2~O

### 上标

上标`x^2^`,x^2^

### 高亮

高亮`==高亮==`，==高亮==

## HTML

`<span style="color:red">this text is red</span>`,<span style="color:red">this text is red</span>

### 嵌入内容

```markdown
<iframe height='265' scrolling='no' title='Fancy Animated SVG Menu' src='https://baidu.com' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'></iframe>
```

<iframe height='265' scrolling='no' title='Fancy Animated SVG Menu' src='https://baidu.com' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'></iframe>
### 视频

`<video src='url'>`

### 其他HTML支持

你可以在 [这里](http://support.typora.io/HTML/)找到细节。







