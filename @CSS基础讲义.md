# css基础

> css 层叠样式表

css是负责描述网页**样式**的语言,可以称为表现层.

## 使用css

### 内联方式(只用于学习)
写在head标签内的style标签内

### 外联 (工作中必须使用)

head标签内 使用 <link href="url.css"></link>

> 注意:使用utf-8编码

### 嵌入 (极少用)
写在标签的style属性内

## 语法

> id class 命名的时候不能使用数字(与特殊字符)开头.

### 基本结构

```
/*属性值通过冒号(:)赋值,每条属性之间使用分号分割*/
选择器   {
            属性名1 : 属性值1 ;
            属性名2 : 属性值2 ;
            属性名3 : 属性值3 ;
            属性名4 : 属性值4 ;
        }
```

### 使用注释

`/**/` 可以进行单行与多行注释


## 选择器

### 基础选择器
- id选择器  `#idName`
- 标签选择器 `tagName`
- class选择器 `.className`

### 基于上下级的选择器

- 派生(后代)选择器  一种基于html结构的选择器 `#two ul li`
- 子选择器  只选择子级的选择器 `#three ul>li`

###  基于兄弟关系的选择器

 - "E+F" 选择E之后的(一个)F
 - "E~F" 选择E之后的(所有)F

### 伪类选择器
 - E:first-child 当E是第一个子级的时候 生效
 - E:last-child 当E是最后一个子级的时候 生效
 - E:target 当选中锚点的时候生效(不常用)
 - E:nth-child(n) 选择一堆兄弟关系的元素中的第n个(注意,不同标签也算兄弟)
    - 2n-1 选择所有的基数
    - 2n  所有的偶数

 - 链接相关伪类,其中 :hover 应用比较广泛

    ```
     /*默认状态*/
            #three:link{
                color: yellow;
            }
            /*悬浮*/
            #three:hover{
                color: red;

            }
            /*激活*/
            #three:active{
                color: #84ff2b;
            }
            /*已访问*/
            #three:visited{
                color: #3a3a3a;
            }

    ```

### 伪元素

"可以理解成写在css内的标签"

div:after{};// div::after{}
div:before{}
相当于为div添加了两个子元素
```
<div>
    <before></before>
        //本来的内容
    <after></after>
</div>
```

常用来处理一些修饰性的内容,比如三角形
还用来处理高度坍塌(最好的方式)

### 属性的继承

所有和布局有关的都不继承:display,float,position,width,

内容相关的,大部分继承,font-size

### CSS的优先级

1. 先计算选择器的优先级
    - !important style属性 1000
    - #id 100
    - .class 10
    - tagname 1
    - "*" 0

```
#id .class ul li{
/*100+10+1+1=112生效*/
}
#id .class li{
/*100+10+1=111*/
}
```


2. 在选择器权重相同的情况下,遵循"就近原则"

```
div{
color:red;
color:blue;/*生效,就近原则*/
}

```

## 属性

### 盒子模型

#### 盒子模型的常用属性

> 注意:只有display:block的元素才能生效宽高

- (内容)宽度 width
- (内容)高度 height
- 填充 padding
- 边框 border

border,padding,margin等属性
- 一个值 代表4个方向都是固定值
- 两个值  上下+左右
- 三个值  上+左右+下
- 四个值 上右下左的顺序写

#### 盒子宽度的计算

> **在默认情况下**,盒子的宽度=  "内容宽+左右padding+左右border"

#### 其他常用的属性
- 盒子与盒子之间的间距 margin
    - 相邻的上下margin会出现融合(谁大取谁的值)
    - (了解即可)爸爸和第一个儿子的margin-top/最后一个儿子的margin-bottom也会出现融合

- 背景色 background:颜色
    - 在背景中使用颜色 background-color:red
    - 在背景中使用图片 background-img:url("url")
    - 平铺 以图片为背景的情况下,会会自动充满整个容器,这个机制叫平铺
           可以通过 `background-repeat`属性来控制
           - repeat-x 只在水平方向平铺
           - repeat-y 只在垂直方向屏幕
           - no-repeat 不平铺(只出现一次)
    - 背景定位 ` background-position` 两个位置作为值 ,\[水平方向,垂直方向\]


    ```
                /*设置背景色*/
                background-color: white;
                /*设置背景图片*/
                background-image: url("img/bgdemo.png");
                /*平铺方向(图片在默认情况下,会自动平铺,充满整个容器)*/
                background-repeat: repeat-x;
                /*背景定位*/
                background-position: top;
    ```


### display 显示

- display:block
    - 把元素当成块状元素处理(独占一行)
    - 宽高可以生效

- display:inline
    - 把元素当成行内元素处理(不独占一行)
    - 宽高不生效

- display:inline-block
    - 内联块(本质还是内联)
    - 宽高生效+不独占一行

- display:none
    - 隐藏
    - 不占据空间
    - 该种显示隐藏不能生效过渡.

### 常用单位

- 长度  px(像素),em(以父级作为参考),rem(以根标签作为参考)
- 时间  s,ms
- 角度  deg
- 颜色  #FFFFFF(颜色的最大值,白色),可以缩写为#fff,  rgb(255,255,255),rgba(255,255,255,0.5),直接使用颜色名

```

#abc=#aabbcc
#123=#112233

```

### 常用属性

- 字体类
```
            /*字号*/
            font-size: 20px;
            /*字体*/
            font-family: 微软雅黑;
            /*颜色*/
            color: red;
            /*字体对齐*/
            text-align: left;
            /*下划线*/
            text-decoration: underline;
            /*斜体*/
            font-style: italic;
            /*行高*/
            line-height:50px ;
            /*粗细*/
            font-weight: 900;
            /*缩进*/
            text-indent: 40px;
```


- 列表

list-style:none

- 处理溢出

overflow:hidden  溢出部分隐藏  ,   overflow:auto

## 浮动布局

浮动是一种跳出文档流(跳半层,容器跳,内容不跳)的布局方式.
在宽度允许的情况下,会尽量向着设置的方向移动

### 浮动的特性

- 容器跳出文档流,但是内容不跳出,浮动元素内容依旧会影响他之后的元素
- 如何一个"爸爸"内的所有"儿子"都浮动,则爸爸的高度不会被撑开,这种现象叫高度坍塌
    - 在最后一个子级元素的下方添加一个块级元素 添加 clear:both(清除浮动)属性
    - 在出现坍塌的元素身上添加 overflow:hidden(本身含义为溢出隐藏,
      有一个附加效果,处理高度坍塌)
    - 给坍塌的元素定高(使用较少)
- 浮动的元素会被当成块状处理(宽高生效)
- 收缩性(利用的不多)

### 处理高度坍塌

- 定高
- 为坍塌的元素添加overflow:hidden
- 坍塌的元素 也添加浮动
- 在坍塌元素的最后一个子级的位置,添加一个"块状"元素,再添加clear:both(清除浮动带来的影响)


## 定位布局

定位是一种完全跳出文档流的布局方式,(绝对,固定)每个元素都会独占一层,
可以通过z-index调整层级顺序(如果重叠,则大的盖住小的,z-index也需要具有定位属性才能生效)

> 绝对定位的元素,left等属性不会生效


- 固定定位fixed
    - 参考窗口进行定位

- 绝对定位absolute
    - 较少用于网格布局,常用于做页面修饰(与特效),其他情况极少使用.

    > "定位父级"(定位+父级):绝对定位的元素在使用left,top,right,bottom属性的时候,会以
    最接近的定位父级(一般来说,是相对定位)作为参考坐标,"固定,相对,绝对,都可以作为定位父级"


    - 与浮动相似的收缩性
    - 会被当成块处理(宽高生效)
    - 比浮动优先级高(同时具有浮动+定位的元素,浮动不生效)
    - 绝对定位的元素可以使用margin来调整位置

- 相对定位relative
    - 相对于自己(相对于该元素本身出现在文档流中的位置来定位)
    - 一般用于限制绝对定位(最常用)
    - 原有的位置,依旧占据空间

- 文档流定位static

## css3--2d转换与过渡

transform:2d转化属性

2d转化属性:

- 位移 translate
- *旋转 rotate
- *拉伸(倍数放大) scale
- 歪斜(ps内的斜切) skew

过渡
transition:变化属性 (变化速度) 时间.

```
div {
transition:left 2s ,width 2s;
}
```

## css3---动画

```
/*
@声明关键字  动画名称 {
        //想要生效变化的样式需要可以进行数值变化,left,width,font-size,color
        状态1 {状态1的属性}
        状态2 {状态2的属性}
}
*/
 @keyframes animate1 {
                0% {
                    left: 0;
                    top: 0;
                    transform: rotate(0deg);
                    background: red;
                }
                25% {
                    background: black;
                    left: 500px;
                    top: 0;
                    transform: rotate(360deg);
                }
            }

```



## css预处理器(了解)

- sass

- less



