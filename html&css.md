#### 浏览器内核
```
    5大浏览器：IE   Chrome  Firefox(火狐)   Safari  Opera
    4个内核：Trident    Chrome、Safari、Opera(Webkit,Blink)    Firefox(Gecko)
```

#### 盒模型
```
    1. 标准盒模型
    盒子的宽高 = 内容content的宽高。
    box-sizing: content-box;

    2. 怪异(IE)盒子模型(我常用)
    盒子的宽高 = 内容content + padding + border
    box-sizing: border-box;

```

#### flex布局
```
    采用 Flex 布局的元素，称为 Flex 容器
    容器的属性：
        flex-direction：决定主轴的方向（即项目的排列方向）
        flex-wrap：决定如何换行。
        flex-flow：flex-direction属性和flex-wrap属性的简写形式
        justify-content：定义了项目在主轴上的对齐方式
        align-items：定义项目在交叉轴上如何对齐
        align-content：定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用

    容器内项目(元素)的属性：
        order：定义项目的排列顺序。数值越小，排列越靠前，默认为0。
        flex-grow：属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。
        flex-shrink：定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。
        flex-basis：定义了在分配多余空间之前，项目占据的主轴空间（main size）。
        flex：是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。
        align-self：属性允许单个项目有与其他项目不一样的对齐方式可覆盖align-items属性。
```

#### 水平/垂直居中
```
    1. 使用flex布局：
        justify-content: center;
        align-items: center;
    
    2. top + margin-top、left + margin-left
        top: 50%;
        left: 50%;
        margin-top: -(元素自身高度的一半);
        margin-left: -(元素自身宽度的一半);

    3. top、left + transform
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);

    4. textAlign + line-height 文字上下左右居中


```

#### BFC
```

```

#### 清除浮动
```
    不清除浮动会引发父元素高度塌陷等问题
    1. 尽量避免使用浮动
    
    clear属性规定元素的哪一侧不允许其他浮动元素

    2. 清浮动方法1
       .clearfloat {
			zoom: 1;
		}

    3. 清浮动方法2(在浮动元素首部或者末尾添加一个隐藏元素，添加clear:both属性)
        .clearfloat {
			display: block;
			clear: both;
			content: "";
			visibility: hidden;
			height: 0;
		}

    4. 清浮动方法3(设置一个伪类，添加clear:both属性)
        .clearfix:after{
            content: '';
            display: block;
            width: 100%;
            clear: both;
            height: 0;
        }

```

#### css动画 和 元素3D效果
```
    1. transition
        1) 需要事件触发，所以没法在网页加载时自动发生
        2) 是一次性的，不能重复发生，除非一再触发
        3) 只能定义开始状态和结束状态，不能定义中间状态，也就是说只有两个状态
        4) 一条transition规则，只能定义一个属性的变化，不能涉及多个属性

    2. animation
        为了解决transition以上这些缺点而提出的
        可以实现多个动画，也可以实现多个动画
        
        单个动画
        animation: 动画名称	 完成动画所花费的时间  动画的速度曲线 动画开始时间 动画播放次数 是否应该轮流反向播放动画

        多个动画
        animation: 第一个动画的参数, 第二个动画的参数, ... , 第n个动画的参数
        
        可以使用贝塞尔曲线控制动画的快慢 cubic-bezier(a,b,c,d) 

    3. transform
        控制元素平移(translate)、放大缩小(scale)、旋转角度(rotate)等
```

#### H5新特性
```
    text-shadow 文字阴影
    box-shadow  边框阴影
```

#### 定位
```
    定位(position) 
	relative: 相对定位, 没有脱离文档流 
	absolute: 绝对定位, 脱离文档流, 向外层查找父元素, 遇到的第一个position: relative;的元素为父元素, 以该父元素的原点为(0,0)定位 
	fixed: 固定定位, 脱离文档流 
	inherit: 继承父元素的position 
	static: 无定位
```

#### rem、em、px、vh、vw的区别
```
    rem: html根节点的font-size的大小 === 1rem 
    em: 父节点的font-size的大小 === 1em	
    px: 像素, 你的物理设备屏幕能显示的最小的点, 不同设备px的长宽不同, 所以会需要做移动端适配	
    vh: 屏幕可视高度 / 100	
    vw: 屏幕可视宽度 / 100	
```

#### src和href的区别
```
    src是引入, 用于替换当前元素, 在请求src资源时会将其指向的资源下载并应用到文档内
    href是引用, 用于在当前文档和引用资源之间确立联系 
```

#### link和@import的区别
```
    link是XHTML标签,除了加载CSS外,还可以定义RSS等其他事务;@import属于CSS范畴,只能加载CSS。
    link引用CSS时,在页面载入时同时加载;@import需要页面网页完全载入以后加载。
    link是XHTML标签,无兼容问题;@import是在CSS2.1提出的,低版本的浏览器不支持。
    link支持使用Javascript控制DOM去改变样式;而@import不支持。
```

#### 雪碧图(css精灵) 和 @font-face
```
    1. 雪碧图
        将多个小图片合成一张
        background-image(背景图片)
		background-position(背景图片定位)
        使用background-position来获取对应的图片
    
    2. icon字体小图标
        特点:
		1. 灵活: 随意改变图标颜色和其他css效果
		2. 矢量性: 图标是矢量的, 与像素无关, 缩放图标不会影响清晰度
		3. 兼容性: 兼容性好
		4. 本地使用
```