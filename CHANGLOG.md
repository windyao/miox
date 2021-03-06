# Miox change logs

> Since the 5.1.11 version, we will provide change logs for each version of the update.

## 5.1.16

- 解决webview跳转时候的`webview:active`事件不触发的问题。

```javascript
@life mounted() {
  this.$on('webveiw:active', () => {
    console.log('webview active');
  })
}
```

## 5.1.15

- `miox-router` 新增`static`方法，用来简化路由队列。
- 为每个新增的webview内嵌一层`.mx-window`节点，用来解决组件第一个元素被直接覆盖样式的问题。

**static**方法演示:

```javascript
route.static({
  '/a/:id': WebviewA,
  '/b/:id': WebviewB,
  ...
})
```

**`.mx-window`** class =>

```html
<div class="mx-app">
  <div class="mx-webviews">
    <div class="mx-webview">
      <div class="mx-window active">
        <div>hello world<p>adfaf</p></div>
      </div>
    </div>
  </div>
</div>
```

## v5.1.14

- 修正`dictionary`中key变量全部字符串化的Bug.

## v5.1.13

- 去掉`index.css`中的`padding` `margin`
- 新增`.inactive`class

## v5.1.12

- 删除`src/miox-convert`模块，因为没有历史包袱，我们不需要使用这个模块。
- `webview:beforeEnter`事件，不再对于新创建webview过程而言，而是对于整个过程而言。因为将要展示的webview必定是存在的。但是可能选取的时候是不存在的。
- 在miox页面切换的时候，增加`.inactive`类，与`.active`对应。同时更新animate.js的动画处理逻辑，使其能够更加自如应对各种情况。
- 修改`miox-css`中的`.mx-webview>*`样式，要求是一个全屏容器。