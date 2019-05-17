### CSS使图片居中的三种方法

#### [参考链接](https://blog.csdn.net/wang414300980/article/details/75089066)

1. #### 第一种方法\(利用display:table-cell\)

```html
 <div class="img_wrap">
　　<img src="wgs.jpg">
 </div>
```

```css
 .img_wrap{
     width: 400px;
     height: 300px;
     border: 1px dashed #ccc;
     display: table-cell; //主要是这个属性
     vertical-align: middle;
     text-align: center;
   }
```

* #### 第二种方法\(采用背景法\)

```html
<div class="img_wrap"></div>
```

```css
.img_wrap{
    width: 400px;
    height: 300px;
    border: 1px dashed #ccc;
    background: url(wgs.jpg) no-repeat center center;
}
```

* #### 第三种方法\(图片外面用个p标签，通过设置line-height使图片垂直居中\)

```html
<div class="img_wrap">
    <p><img src="wgs.jpg"></p>
 </div>
```

```css
*{margin: 0px;padding: 0px}
  .img_wrap{
      width: 400px;
      height: 300px;
      border: 1px dashed #ccc;
      text-align: center;}
  .img_wrap p{
      width:400px;
      height:300px;
      line-height:300px;  /* 行高等于高度 */
 }
 .img_wrap p img{
     *margin-top:expression((400 - this.height )/2);  /* CSS表达式用来兼容IE6/IE7 */
      vertical-align:middle;
      border:1px solid #ccc;
 }
```



