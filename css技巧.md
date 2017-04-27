# css技巧

## 盒子相关属性1111

### 使用border制作三角形

- 宽高为0
- display:block(宽高生效)
- 指定三条边隐藏,显示一条
- 一般配合定位使用

```
        元素 {
            display: block;
            width: 0px;
            height: 0px;
            /*设置4条边隐藏*/
            border: 20px solid transparent;

            /*选择需要的方向显示*/
            /*border-top-color: #fff238;*/
            /*border-left-color: #84291d;*/
            /*border-right-color: #398429;*/
            border-bottom-color: #5676ff;

        }
```

### 画圆形
- 创建一个正方形
- border-radius(圆角属性)  设置 取值为宽度一半(最小)


```
元素 {
            display: block;
            background: red;
            width: 200px;
            height: 200px;
            border-radius: 100px;
 }
```

### margin

- "能用padding解决的就用padding"
- 上下margin有可能出现融合
- 内联元素的上下margin不生效
- 对一个有宽度的块状元素,在父级宽度允许的情况下可以使用margin:0 auto水平居中
- margin的值可以是负的. 有可能产生元素的覆盖.
- 绝对定位的元素,在使用left等属性控制位置的基础上,还可以使用margin-left补充定位,可以实现一个绝对定位的元素相对于定位父级居中.



### css sprite/css精灵/雪碧图

将网页中的小图片(icon)保存成一张图,通过背景定位,来控制具体显示哪一部分的技术

雪碧图所用到的属性
```
 .sprite {
            display: block;
            width: 100px;
            height: 100px;
            background-image: url("img/icon.png");
            background-repeat: no-repeat;
            overflow: hidden;
            background-position: 0px 0px;
        }
```

优点

- 小图标集中管理,方便调用
- 降低服务器负担(通过降低连接数的方式)

应用范围

只适合图标这种尺寸比较小,经常使用的网页元素


### 关于(水平)居中

- display:block
    - margin:0 auto

- diplay:inline/inlien-block
    - 可以给父级设置text-algin:center

- 定位相关
    - left:50% ;margin-left:自身宽度的一半.

### 关于(垂直)居中

- 居中内联元素
    - 设置line-height=父级高度

- 绝对定位的前提下,top:50%,margin-top:自身高度的一半

## 定位相关

### "四点"定位

将一个绝对定位的元素,没有宽高的情况下,同时设置left,与right就能拉伸出"宽度".

### 不指定定位父级的绝对定位

为一个元素添加绝对定位,同时不指定相对父级.使用margin来完全left,top值的功能.
但是不使用left,top等参数的一种定位高级用法.

## 浮动相关

浮动是一种跳出文档流的布局方式,所以
如果一个父级的"所有"子级都浮动了(不论左右),则在父级看来,所有的子集都"不存在"

会出现父级的高度无法靠子级"撑开",这种情况叫"高度坍塌",这种情况"极为"常见.

处理高度坍塌:

- 定高
- 坍塌的元素给 overflow:hidden(触发bfc)
- 坍塌的元素给 浮动(触发bfc)
- 在最后一个子级的位置添加一个"块状"元素同时添加"clear:both".
- "最好的方式",提前写好处理高度坍塌的类`.clear`,为可能坍塌的元素添加  `.clear`

```
.clear:after{
    content:"";
    display:"block";
    clear:both;
}

```

