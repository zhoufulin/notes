## CSS Transition

1、**transition**的作用在于，指定状态变化所需要的时间。

```css
img{
    transition: 1s;
}
```

还可以指定transition适用的属性，比如只适用于height。

```css
img{
    transition: 1s height;
}
```





2、**transition-delay**指定了动画发生的顺序，使得多个不同的transition可以连在一起。

```css
img{
    transition: 1s height, 1s 1s width;
}
```

上面代码指定，width在1秒之后，再开始变化，也就是延迟（delay）1秒。



3、**transition-timing-function**，transition的状态变化速度（又称timing function），默认不是匀速的，而是逐渐放慢，这叫做ease。

```css
img{
    transition: 1s ease;
}
```

除了ease以外，其他模式还包括

```markdown
（1）linear：匀速
（2）ease-in：加速
（3）ease-out：减速
（4）cubic-bezier函数：自定义速度模式
```

cubic-bezier即[贝赛尔曲线](http://www.jianshu.com/p/d999f090d333)，可以通过[工具网站](http://cubic-bezier.com/#.13,.93,.78,.55)来定制



4、**transition**的各项属性。

```css
transition: property duration timing-function delay;
```

- [transition-property](http://www.w3school.com.cn/cssref/pr_transition-property.asp) : 规定设置过渡效果的 CSS 属性的名称。
- [transition-duration](http://www.w3school.com.cn/cssref/pr_transition-duration.asp) : 规定完成过渡效果需要多少秒或毫秒。
- [transition-timing-function](http://www.w3school.com.cn/cssref/pr_transition-timing-function.asp) : 规定速度效果的速度曲线。
- [transition-delay](http://www.w3school.com.cn/cssref/pr_transition-delay.asp) : 定义过渡效果何时开始。



## CSS Animation

**1、基本用法**

首先，CSS Animation需要指定动画一个周期持续的时间，以及动画效果的名称。

```css
div:hover {
  animation: 1s rainbow;
}
```

再用keyframes关键字，定义rainbow效果。下面代码表示，rainbow效果一共有三个状态，分别为起始（0%）、中点（50%）和结束（100%）。如果有需要，完全可以插入更多状态。

```css
@keyframes rainbow {
  0% { background: #c00; }
  50% { background: orange; }
  100% { background: yellowgreen; }
}
```

可以指定动画具体播放的次数，比如3次或者无限次。

```css
div:hover {
  animation: 1s rainbow 3;
  /*animation: 1s rainbow infinite;*/
}
```



**2、animation-fill-mode**

动画结束以后，会立即从结束状态跳回到起始状态。如果想让动画保持在结束状态，需要使用animation-fill-mode属性。

```css
div:hover {
  animation: 1s rainbow forwards;
}
/* forwards表示让动画停留在结束状态。*/
```

animation-fill-mode还可以使用下列值。

```markdown
（1）none：默认值，回到动画没开始时的状态。
（2）backwards：让动画回到第一帧的状态。
（3）both: 根据animation-direction（见后）轮流应用forwards和backwards规则。
```



**3、animation-direction**

动画循环播放时，每次都是从结束状态跳回到起始状态，再开始播放。animation-direction属性，可以改变这种行为。

默认情况是，animation-direction等于normal。取reverse即反向循环。

```css
div:hover {
  animation: 1s rainbow 3 normal;
}
```



**4、animation的各项属性**

同transition一样，animation也是一个简写形式。

```css
div:hover {
  animation: raibow 5s linear 2s infinite alternate;
}
```

- [animation-name](http://www.w3school.com.cn/cssref/pr_animation-name.asp) : 规定 @keyframes 动画的名称。
- [animation-duration](http://www.w3school.com.cn/cssref/pr_animation-duration.asp) : 规定动画完成一个周期所花费的秒或毫秒。默认是 0。
- [animation-timing-function](http://www.w3school.com.cn/cssref/pr_animation-timing-function.asp) : 规定动画的速度曲线。默认是 "ease"。
- [animation-delay](http://www.w3school.com.cn/cssref/pr_animation-delay.asp) : 规定动画何时开始。默认是 0。
- [animation-iteration-count](http://www.w3school.com.cn/cssref/pr_animation-iteration-count.asp) ：规定动画被播放的次数。默认是 1。
- [animation-direction](http://www.w3school.com.cn/cssref/pr_animation-direction.asp) ： 规定动画是否在下一周期逆向地播放。默认是 "normal"。
- [animation-play-state](http://www.w3school.com.cn/cssref/pr_animation-play-state.asp) ：规定动画是否正在运行或暂停。默认是 "running"。
- [animation-fill-mode](http://www.w3school.com.cn/cssref/pr_animation-fill-mode.asp) ： 规定对象动画时间之外的状态。



**5、keyframes的写法**

0%可以用from代表，100%可以用to代表。

```css
@keyframes rainbow {
  from { background: #c00 }
  50% { background: orange }
  to { background: yellowgreen }
}
```



**6、animation-play-state**

有时，动画播放过程中，会突然停止。这时，默认行为是跳回到动画的开始状态。

如果想让动画保持突然终止时的状态，就要使用animation-play-state属性。

```css
div {
    animation: spin 1s linear infinite;
    animation-play-state: paused;
}

div:hover {
  animation-play-state: running;
}
```

