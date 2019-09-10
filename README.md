# Mirages_Modify
> Mirages

使用这款主题也已经很久了，主题的简约美貌很令人喜爱。但也无法阻挡自己动手DiY的喜好，虽然在上个Wordpress主题中已经动手到自己都觉得难看的地步，但是我还是打算继续常识瞎改。

如下是瞎改手记：

## #footer

	今天在`footer`中看到一个裙子，觉得加载页脚还是挺好看的，于是就正大光明的借过来了。

![1568013294503.png][1]

> 当然光借鉴不学习是不能够有进步的。

当初naive的我以为只需要在`footer`上直接上个背景图，就简单的解决问题了。当然是我想的太简单了。

首先问题的主要是裙边从视觉角度来看是从`body`衍生了一点到颜色不同的区域`footer`中。那简单插入一个背景图就不能那么顺利的解决问题了。

那么我们可以使用在`footer`中，copyright上加一个`div`，该`div`并不需要实际在`body`和`footer`中间，我们是直接在copyright上方创建的这个`div`，后续使用元素将它的背景图漂移到与copyright和`body`重叠的区域就可以了。

### 如何漂移

这是对于我一个几乎没有前端知识入门玩家的很大的问题，css有超多种玩法，让一个div带着背景漂移当然是一个很简单的事情。在借鉴大佬的成果下， 自己研究了一下：在给予`height`值后，使用`position`配合`bottom`就能轻松漂移到copyright的上方。

`bottom`的效果取决于元素的`position`属性：

- 当`position`设置为`absolute`或`fixed`时，`bottom`属性指定了定位元素下外边距边界与其包含块下边界之间的偏移。
- 当`position`设置为`relative`时，`bottom`属性指定了元素的下边界离开其正常位置的偏移。
- 当`position`设置为`sticky`时，如果元素在viewport里面，`bottom`属性的效果和position为`relative`等同；如果元素在viewport外面，`bottom`属性的效果和position为`fixed`等同。
- 当`position`设置为`static`时，`bottom`属性无效。

详细操作：

添加一个在`footer`中的`div`，并赋予以下css值

```css
background: url(/images/footer.png) no-repeat 50%;
height: 360px;
z-index: 100;
position: absolute;
bottom: 1px;
width: 100%;
pointer-events: none;
```

`background no-repeat `：背景不重复

`height`：设定高度

[`z-index`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/z-index)：对于一个已经定位的元素（即position属性值不是static的元素），z-index 属性指定元素在当前堆叠上下文中的堆叠层级

[`position`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position)：用于指定一个元素在文档中的定位方式

[`bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/bottom)：定义了定位元素下外边距边界与其包含块下边界之间的偏移，非定位元素设置此属性无效

`width`：宽度

`pointer-events`：指定在什么情况下 (如果有) 某个特定的图形元素可以成为鼠标事件的 target

当然，如果直接漂移，可能会与`body`中的内容重叠，就如下效果。直接导致了遮住了主题中的文字。所以为了防止`body`被遮住，我们还需要再`body`的下方再创建一个`div`用来给我们的背景图“漂移”。

![1568014548234.png][2]

并且背景使用和`body`一样的颜色，给人从视觉上感觉裙边是衍生到下面的copyright上的。

操作：

在上述`div`上方添加一个`div`并赋予以下css

```css
padding: 6.6rem;
background: white;
```

其他记录：

```
<div id="dup"></div>
<div id="dress"></div>
```

## 更新主题

> 自家用

无论是怎么修改主题到自己想要的样子，但是最终开发的人不是我，目前也没有能力继续把一个主题维护下去。所以更新是必不可免的，但是更新主题必然会遇到个问题，主题不过是几个单个文件，自己修改就是在修改这些文件，而这些单个文件是不能够增量更新的，既然自己手动修改过了，那么新版本的主题必将覆盖我自己所修改的一些地方。每次遇到的问题都是忘记自己到底在哪里瞎改了，更新完了之后各种问题。

所以决定动了哪些文件还是记一下吧。

- **footer.php**：/usr/themes/Mirages/component
  - 页脚裙边
- **xfy.css**：
  - 主要的自定义样式

## ToDo

	当然这只是一部分，0基础的我不能够在短时间内将它完全变成我想要的样子，而且随着时间的变化，自己对于美的定义也是会变化的。

- [ ] 首页标题添加一些动画
- [ ] “阅读全文”按钮添加动画
- [ ] Live2d！
- [ ] 选中文字变色
- [ ] 让裙子自适应且居中
- [x] 鼠标指针

## 日志

2019-9-10：修改鼠标指针。

2019-9-10：添加页脚裙边，修改相应的css。

[1]: https://cdn.defectink.com/usr/uploads/2019/09/10/1568013294503.png-shuiyin
[2]: https://cdn.defectink.com/usr/uploads/2019/09/10/1568014548234.png-shuiyin