# ✏️ Markdown 語法

## 標題

```
語法：
# H1
## H2
### H3
#### H4
##### H5
###### H6
```

如果要如果要在標題添加`id`或`class`：

```
語法：
# This is H1 with one id {#my_id}
## This is H2 with two classes {.class1 .class2}
```

## 強調

_斜體_
`語法：*斜體* 或 _斜體_`
**粗體**
`語法：**粗體** 或 __粗體__`
~~刪除~~
`語法：~~刪除~~ 或 <del>刪除</del>`
==標記==
`語法：==標記==`
上標^th^
`語法：^th^`
下標~2~
`語法：~2~`

## 列表

#### 無序列表

- Red
- Green
- Blue

```
語法：
* Red
* Green
* Blue
或
+ Red
+ Green
+ Blue
或
- Red
- Green
- Blue
```

#### 有序列表

```
語法：
1. Meat
2. Vegetable
3. Fruit:
   1. apple
   2. watermelon
```

## 任務列表

- [x] Today
- [x] Yesterday
- [ ] Tomorrow

```
語法：
- [x] Today
- [x] Yesterday
- [ ] Tomorrow
```

## 水平線

---

```
語法：*** 或 --- 或 ___
```

## 超連結

#### 外部連結

[GitHub](https://github.com)

```
語法：
[GitHub](https://github.com)
或
<https://github.com>
```

Login by [Google][1] or [FaceBook][2] or [Apple][3].

[1]: http://google.com/ "Google"
[2]: http://facebook.com/ "FaceBook"
[3]: http://apple.com/ "Apple"

```
語法：
Login by [Google][1] or [FaceBook][2] or [Apple][3].

[1]: http://google.com/    "Google"
[2]: http://facebook.com/  "FaceBook"
[3]: http://apple.com/     "Apple"
```

## 添加圖片

```
語法：
![GitHub logo](https://github.com/gitlogo.jpg "git圖示")
```

## 添加影片

```
語法：
<iframe src="https://www.youtube.com/embed/GIP0j4oRMWc" width="420" height="315"></iframe>
```

## 區塊

`小區塊用一個` `

````
大區塊用三個```
````

## 引用

> 可以放引言或是
>
> > 當作縮排(有階層)

```
語法：
>可以放引言或是
>>當作縮排(有階層)
```

## 腳註

Content [^1] (註解會在文章結尾)
[^1]: Hi! This is a footnote

```
Content [^1]
[^1]: Hi! This is a footnote
```

## 表格

| Header 1 | Header2 |
| -------- | ------- |
| A        | B       |
| C        | D       |

```
語法：
Header 1 | Header2
---------|--------
A        | B
C        | D
```

## 代碼塊

#### 語法高亮

```js
function sayHi() {
  console.log("Hello World");
}
```

````
語法：
```js
function sayHi(){
    console.log("Hello World")
}
```
````

#### 代碼行數

```js {.line-numbers}
function sum(a, b) {
  return a + b;
}
```

````
語法：
```js  {.line-numbers}
function sum(a, b) {
  return a + b
}
```
````

#### 高亮代碼行數

```js {highlight=[2-3,5]}
function rgbToHex(r, g, b) {
  const toHex = [r, g, b]
    .map((item) => Number(item).toString(16).toUpperCase().padStart(2, 0))
    .join("");
  return `#${toHex}`;
}
```

````
語法：
```js {highlight=[2-3,5]}
function rgbToHex(r, g, b) {
  const toHex = [r, g, b]
    .map((item) => Number(item).toString(16).toUpperCase().padStart(2, 0))
    .join("");
  return `#${toHex}`;
}
```
````

## 參考

- [Basic formatting Syntax](https://docs.github.com/zh/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
- [Markdown 基本要素](https://shd101wyy.github.io/markdown-preview-enhanced/#/zh-tw/markdown-basics)
- [Markdown 風格](https://kingofamani.gitbooks.io/git-teach/content/chapter_6_gitbook/markdown.html)
