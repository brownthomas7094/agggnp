新宝3官方代理【Q-——333307——】新宝3官方代理【 辋芷《888yx●vip》 】
新宝3官方代理【Q-——333307——】新宝3官方代理【 辋芷《888yx●vip》 】

 前端开发必备：一次学会防抖与节流，让你的网站性能直接拉满

你是否遇到过这样的场景？用户在搜索框里疯狂输入，结果后端接口被请求刷爆；页面滚动时频繁触发计算，导致卡顿掉帧。别急，今天咱们就来聊聊前端性能优化的两大神器——防抖（Debounce） 和节流（Throttle）。这两个概念是前端面试的高频题，也是实际开发中提升用户体验的关键手段。读完这篇，你不仅能搞懂原理，还能直接抄作业。

 1. 什么是防抖？它解决什么问题？

防抖的核心思想：在事件被连续触发时，只在最后一次触发后的指定时间内执行回调。如果在这段时间内再次触发，则重新计时。

典型应用场景：
- 搜索框输入联想（用户停止输入后再请求）
- 窗口Resize结束后的计算
- 表单提交按钮（防止多次提交）

想象一下，用户每次按键都发一个Ajax请求，服务器会很不开心。使用防抖后，只有当用户停下来的那刻，才会发出请求，大大节省资源。

 2. 什么是节流？它和防抖有何不同？

节流（Throttle）的核心思想：在一个时间窗口内，无论事件触发多少次，回调函数只执行一次。就像一个阀门，控制水流速度。

典型应用场景：
- 页面滚动监听（懒加载、滚动进度）
- 鼠标移动事件（Canvas绘制、游戏逻辑）
- 浏览器拖动、缩放

比如你监听滚动事件去计算位置，如果不做处理，一秒可能触发60次。用节流后，规定每500ms执行一次，浏览器就不会感到“窒息”。

 3. 手写核心代码（带注释）

先看防抖（支持立即执行版本）：
```javascript
function debounce(func, wait, immediate) {
  let timer = null;
  return function() {
    const context = this;
    const args = arguments;
    if (timer) clearTimeout(timer);
    if (immediate) {
      const callNow = !timer;
      timer = setTimeout(() => timer = null, wait);
      if (callNow) func.apply(context, args);
    } else {
      timer = setTimeout(() => func.apply(context, args), wait);
    }
  }
}
```
节流（时间戳和定时器结合版）：
```javascript
function throttle(func, wait) {
  let previous = 0;
  let timer = null;
  return function() {
    const now = Date.now();
    const remaining = wait - (now - previous);
    const context = this;
    const args = arguments;
    if (remaining <= 0) {
      // 如果间隔够了就立即执行
      if (timer) clearTimeout(timer);
      previous = now;
      func.apply(context, args);
    } else if (!timer) {
      // 否则设置定时器，保证最后一次触发能执行（尾随模式）
      timer = setTimeout(() => {
        previous = Date.now();
        func.apply(context, args);
        timer = null;
      }, remaining);
    }
  }
}
```

 4. 你能得心应手？看这几个进阶技巧

- lodash的运用：其实Lodash库早已封装了`_.debounce`和`_.throttle`，功能更完善。但理解原理才能更好的调参（如`leading`、`trailing`选项）。
- React/Vue中使用：在Vue中需在`beforeDestroy`钩子中清除定时器，在React中则用`useRef`保存定时器并在`useEffect`的清理函数里清除，防止内存泄漏。

 5. 互动时间：你想知道什么？

上面代码里的细节你Get到了吗？有没有踩过什么坑？比如定时器thistle一起用，或者关于`leading`和`trailing`的效果差异，欢迎在评论区留言或私信讨论。觉得有收获的话，动动小手点个“在看”，或者分享给正在写代码的朋友，我们旨在让更多人写出丝滑的代码！下期你想看什么？是“手写Promise串联”还是“SSR原理实战”？评论区告诉我。

相关推荐：

https://github.com/pattersonnathan432/swwvgy/blob/main/ch%E1%BB%8Di%20g%C3%A0%20%F0%9F%90%94%20%EF%BC%9A%E6%96%B0%E5%AE%9D3%E5%B9%B3%E5%8F%B0%E7%99%BB%E5%BD%95_%E6%89%9B%E8%93%9F%E6%85%95%E7%85%A7%E5%9E%A2sylee.md

<img src="https://i.postimg.cc/3NvfSyM8/mei-nu-bei-jing-zhao-shang-tu-zhi-zuo-(22).png" />

相关推荐：

https://github.com/pattersonnathan432/swwvgy/commit/eb2b3e4998aaa26629e2929f9a5ad5a15fe635b3

<img src="https://i.postimg.cc/3NvfSyM8/mei-nu-bei-jing-zhao-shang-tu-zhi-zuo-(22).png" />
相关推荐：

https://github.com/caseylauren602/rqzbiq/blob/main/C%E1%BB%91c%20Games%20%F0%9F%A5%8A%EF%BC%9A%E6%96%B0%E5%AE%9D3%E5%B9%B3%E5%8F%B0%E5%9C%B0%E5%9D%80_%E6%A2%A6%E8%82%A5%E9%82%91%E6%88%98%E4%B9%8Cykqcp.md

<img src="https://i.postimg.cc/fLFgfcPy/mei-nu-bei-jing-zhao-shang-tu-zhi-zuo-(21).png" />
相关推荐：

https://github.com/caseylauren602/rqzbiq/commit/809ac5f31e334c78cdb8568b4d548553f2494233

<img src="https://i.postimg.cc/BbK7Y8Wv/mei-nu-bei-jing-zhao-shang-tu-zhi-zuo-(23).png" />

资讯来源：新华网、人民网、央视新闻、中新网、凤凰网、澎湃新闻、界面新闻、新浪新闻、搜狐网、财新网、观察者网、第一财经等主流平台，以独树一帜的观察视角与扎实的深度报道能力，在资讯领域收获广泛关注。
