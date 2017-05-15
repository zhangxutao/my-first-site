### 移动端开发为什么不使用jquery
    1.jquery体积大  
    2.jquery做了大量的兼容  没有必要  都是高版本浏览器
    并不是说一定不用  最好不要用

### 搜索效果
```javascript
var search = function(){
    /*
    * 1.页面初始化的时候  距离顶部是0的距离的时候  透明度是0
    * 2.当页面滚动的时候  随着页面距离顶部的距离变大  透明度变大
    * 3.当滚动的距离超过了轮播图的距离的时候 保持不变
    * */
    /*获取dom元素*/
    var search = document.querySelector('.jd_search_box');
    var banner = document.querySelector('.jd_banner');
    /*距离范围*/
    var height = banner.offsetHeight;

    /*监听滚动事件*/
    window.onscroll = function() {

        /*当前页面滚动的距离*/
        var top = document.body.scrollTop;
        /*谷歌*/
        /*var top = document.documentElement.scrollTop;/!*ie*!/*/

        var opacity = 0;

        if (top > height) {
            /*3.当滚动的距离超过了轮播图的距离的时候 保持不变*/
            opacity = 0.85;
        } else {
            /*2.当页面滚动的时候  随着页面距离顶部的距离变大  透明度变大*/
            opacity = 0.85 * (top / height);
        }

        /*设置颜色给搜索盒子*/
        search.style.background = 'rgba(216,80,92,'+opacity+')'
    }

}
```

### touch事件  

介绍：
移动端特有事件，触屏设备特有的事件,android,ios设备。

**touchstart**
手指刚刚触摸到屏幕的时候  触发的事件

**touchmove**
手指在屏幕上滑动的时候  会不停的触发

**touchend**
手指离开平屏幕的时候   触发的事件

touchcancel
被迫终止（来电）滑动  触发的事件


使用这些事件 怎么
绑定：on  但是第二次会覆盖
     
```javascript
        /*给div绑定touch事件*/
        var dom = document.querySelector('div');

        /*touchstart*/
        /*dom.attachEvent(); ie*/
        /*手指刚刚触摸到屏幕的时候  触发的事件*/
        dom.addEventListener('touchstart',function(){
            console.log('touchstart');
        });
        /*手指在屏幕上滑动的时候  会不停的触发*/
        dom.addEventListener('touchmove',function(){
            console.log('touchmove');
        });
        /*手指离开平屏幕的时候   触发的事件*/
        dom.addEventListener('touchend',function(){
            console.log('touchend');
        });

```
滑动效果分析
依靠touch相关事件，根据触摸位置的改变，改变对应元素的位移translate

1.怎么监听位置的改变
2.怎么获取当前的坐标
3.计算位移再设置滑动

触摸点的集合  记录触摸点的
changedTouches
当前最新改变的触摸点集合   整个事件都会有changedTouches记录
targetTouches
记录当前元素上面的所有触摸点集合     touchend没有记录
touches
记录页面上所有的触摸点集合           touchend没有记录


获取坐标：

clientX
clientY
基于当前视口触摸点的坐标
pageX
pageY
基于当前页面触摸点的坐标
screenX
screenY
基于当前屏幕触摸点的坐标   



### 轮播图

理解 transitionend  animationend

代码见案例

衍生出  左滑和右滑 手势事件


### 倒计时

代码见案例



### 移动端滑动效果

滑动效果分析
依靠touch相关事件，根据触摸位置的改变，改变对应元素的位移translate

### 移动端轻触事件

tap 轻触

移动端的click事件有关系
移动端有没有click事件有

click事件在移动端的特点：300ms左右延时

问题：造成响应过慢  用户体验下降
解决：方案有两个

方案一  tap(是比click响应更快的事件)  touch衍生
        
        zepto移动端的js库 包含了 tap事件

方案二  插件  fastclick

FastClick是一个非常方便的库,在移动浏览器上发生介于轻敲及点击之间的指令时,能够让你摆脱300毫秒的延迟




### 移动端手势事件

左滑和右滑 手势事件
上滑和下滑 手势事件


### 列表（分类）页面

两栏自适应的方案  
一侧固定宽度浮动  另一侧设置 overflow：hidden
www.zhangxinxu.com/wordpress/2015/02/css-deep-understand-flow-bfc-column-two-auto-layout/




### 区域滚动插件

iscroll