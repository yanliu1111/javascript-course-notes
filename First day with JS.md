# First day with JS

2022-08-25

## Typora

### 对文字的特殊标注

#### 标题

一个＃子键，heading1 根据不同themes不同快捷建

##🎧二级标题

一级到六级标题

#### 下划线

<u></u>

<u>测试效果</u>

ctrl+u

<u>测试效果</u>

#### 强调 

前后两个*

**测试效果**

#### 斜体

前后一个*

*测试效果*

#### 删除

转化半角输入，英文

前后两个~

~~测试效果~~

#### 方框

转化半角输入，英文

前后1个`

`测试一下，框起来啦`

#### 注释

[^1]  前面不加冒号，后面加：就是注释

今天吃啥[^1]

[^1]:今天吃🐟

#### 高亮

前后两个=就是高亮

==测试效果==

#### 角标

上角标^下角标~ 注意是前后两个

H~2~O

X^2^

行内输入数学公式 两个$符号

$x^2+y_1$

y_1

#### 转义

斜线\ 加后面的特殊符号就是本意输出,注意==斜线方向==

### List

#### 有序

1. 

2. 
3. 

#### 无序

+-*空格都是一样的

* 啊啊啊
  * tab按键可以缩进下一级list
  * shift+tab回到上一级
* 我我我
* 你你你
* 他他他

#### todo list

-空格【空格】

- [ ] JavaScript
- [ ] React
  - [ ] VUE
- [ ] HTML
- [ ] CSS
- [ ] Python
  - [ ] Flask

### Table

#### ctrl+t

| 周一      | 周二 | 周三 | 周四 | 周五 |
| --------- | ---- | ---- | ---- | ---- |
| 7am-9am   |      |      |      |      |
| 10am-12am |      |      |      |      |
| 1pm-5pm   |      |      |      |      |

| sort-and-count(L)                |
| :------------------------------- |
| If the list has one element then |
| there are no inversions          |
| Else                             |



### 分割线

\----

----

\***

***

### 插入

#### 图片

drag

#### 链接

[youtube](https://www.youtube.com/watch?v=tIUmf7SUIwM)

中括号加小括号

#### 数学公式

2个$回车，latex同
$$
f(x)=\frac{1}{\sqrt{2\pi}\sigma}exp(-\frac{(x-\mu)^2}{2\sigma^2})
$$
​	Bernoulli: $p(x)=p^x(1-p)^{1-x}$

在一段话加入公式就是两个$中间加入

#### CODE

\```

```javascript
function testGreaterOrEqual(val) {
  if (val>=20) {  // Change this line
    return "20 or Over";
  }
  if (val>=10) {  // Change this line
    return "10 or Over";
  }
  return "Less than 10";
}
testGreaterOrEqual(10);

```



#### 表情

：加关键词

:sweat:

:happy:

:beer:

#### 引用

大于号

>**JavaScript** ([/ˈdʒɑːvəskrɪpt/](https://en.wikipedia.org/wiki/Help:IPA/English)),[[10\]](https://en.wikipedia.org/wiki/JavaScript#cite_note-10) often abbreviated **JS**, is a [programming language](https://en.wikipedia.org/wiki/Programming_language) that is one of the core technologies of the [World Wide Web](https://en.wikipedia.org/wiki/World_Wide_Web), alongside [HTML](https://en.wikipedia.org/wiki/HTML) and [CSS](https://en.wikipedia.org/wiki/CSS).[[11\]](https://en.wikipedia.org/wiki/JavaScript#cite_note-js_definitive-11)

shif+F12 基于chrom的开发者工具栏

#### 目录

\[toc]+enter

[TOC]

###  VS code 快捷键

1. Ctrl+alt+e   toggle max panel

2. Ctrl+shift+k      Delete Line

3. Ctrl+P     Search file by name

4. Ctrl+enter    打开在第二个页面

5. Ctrl+shift+f    Find in files 例如 那些文件包含了“add_tag”字串

6. Ctrl+W     Close a tab

7. Shift+Ctrl + t      Reopen a tab

8. Ctrl + 鼠标左键    Open definition

9. Ctil+ - Go back

10. Alt + Ctrl+鼠标左键    Open definition in a split window

11. Shift+alt+downarrow       Copy Line Down

    Shift+alt+downarrow        Copy Line Up

12. Ctrl+G   go to line number

13. Shift + Ctrl + -/+ zoom in and out

14. ctrl+/ change to comment

15. MacOS: CMD + CTRL +space 

    Win10: windows + . 

    show all emoji

16. Ctrl + D, 如果选择一个variable, 需要改变，按两键后，会把所有此variable选择，可以一起修改。

17. window+alt+up/down:  change lines up and down

    option in mac = window in PC

18. shift + alt + up 上面添加一行一样的。copy on the up line



leetcode YanLiu0504, 820504Ly!

























