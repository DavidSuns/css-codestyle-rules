# CSS代码规范

### 1.代码风格

>* 使用soft-tab（两个空格），保证代码在各种环境下显示一致。
>* 使用小写字母，复合词以 - 分隔。
>* 使用组合选择器时，保持每个独立的选择器占用一行。

```css
/* Bad CSS */
.selector, .selector-secondary, .selector[type=text] {
  ...
}

/* Good CSS */
.selector,
.selector-secondary,
.selector-third {
  ...
}
```
>* 声明块的右括号应该另起一行。
>* 每条声明 : 后应该插入一个空格。
>* 每条声明应该只占用一行来保证错误报告更加准确。
>* 所有声明应该以分号结尾。虽然最后一条声明后的分号是可选的，但是如果没有他，你的代码会更容易出错。
>* 逗号分隔的取值，都应该在逗号之后增加一个空格。
>* 不要在属性取值或者颜色参数前面添加不必要的 0 (比如，使用 .5 替代 0.5 和 -.5px 替代 0.5px)。
>* 所有的十六进制值都应该使用小写字母，例如 #fff。因为小写字母有更多样的外形，在浏览文档时，他们能够更轻松的被区分开来。
>* 尽可能使用短的十六进制数值，例如使用 #fff 替代 #ffffff。
>* 不要为 0 指明单位，比如使用 margin: 0; 而不是 margin: 0px;。
>* 尽量少使用元素选择器（性能考虑），谨慎使用id选择器（规则优先级高，不易覆盖，重用性不好）。
>* 使用 .js-* classes 来表示行为(相对于样式)，但是不要在 CSS 中定义这些 classes。
>* 避免过度使用简写。.btn 可以很好地描述 button，但是 .s 不能代表任何元素。
>*  带私有前缀的属性由长到短排列，按冒号位置对齐。

```css
.box {
  -webkit-box-sizing: border-box;
     -moz-box-sizing: border-box;
          box-sizing: border-box;
}
```
>* 禁用表达式（性能考虑）
在一个声明块中只包含一条声明的情况下，为了易读性和快速编辑可以考虑移除其中的换行。所有包含多条声明的声明块应该分为多行。例：

```css
/* Single declarations on one line */
.span1 { width: 60px; }
.span2 { width: 140px; }
.span3 { width: 220px; }
```
>* 给css规则模块添加注释。
>* 在sass中，避免不必要的嵌套。可以进行嵌套，不意味着你应该这样做。只有在需要给父元素增加样式并且同时存在多个子元素时才需要考虑嵌套。

```css
/* Without nesting */
.table > thead > tr > th { … }
.table > thead > tr > td { … }

/* With nesting */
.table > thead > tr {
  > th { … }
  > td { … }
}
```


### 2.声明顺序

>* 相关的属性声明应该以下面的顺序分组处理：

>> Positioning
>> Box model 盒模型
>> Typographic 排版
>> Visual 外观

```css
.declaration-order {
  /* Positioning */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;

  /* Box-model */
  display: block;
  float: right;
  width: 100px;
  height: 100px;

  /* Typography */
  font: normal 13px "Helvetica Neue", sans-serif;
  line-height: 1.5;
  color: #333;
  text-align: center;

  /* Visual */
  background-color: #f5f5f5;
  border: 1px solid #e5e5e5;
  border-radius: 3px;

  /* Misc */
  opacity: 1;
}
```

### 3.媒体查询

>* Media Query 不得单独编排，必须与相关的规则一起定义。

```css
/* Good */
/* header styles */
@media (...) {
    /* header styles */
}

/* main styles */
@media (...) {
    /* main styles */
}

/* footer styles */
@media (...) {
    /* footer styles */
}


/* Bad */
/* header styles */
/* main styles */
/* footer styles */

@media (...) {
    /* header styles */
    /* main styles */
    /* footer styles */
}
```

### 4.属性简写

坚持限制属性取值简写的使用，属性简写需要你必须显式设置所有取值。常见的属性简写滥用包括:

>* padding
>* margin
>* font
>* background
>* border
>* border-radius

大多数情况下，我们并不需要设置属性简写中包含的所有值。例如，HTML 头部只设置上下的 margin，所以如果需要，只设置这两个值。过度使用属性简写往往会导致更混乱的代码，其中包含不必要的重写和意想不到的副作用。

```css
/* Bad example */
.element {
  margin: 0 0 10px;
  background: red;
  background: url("image.jpg");
  border-radius: 3px 3px 0 0;
}

/* Good example */
.element {
  margin-bottom: 10px;
  background-color: red;
  background-image: url("image.jpg");
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
}
```
