## Notification 通知

悬浮出现在页面右上角，显示全局的通知提醒消息。

### 基本用法

适用性广泛的通知栏

::: demo Notification 组件提供通知功能，Element 注册了`$notify`方法，接收一个`options`字面量参数，在最简单的情况下，你可以设置`title`字段和`message`字段，用于设置通知的标题和正文。默认情况下，经过一段时间后 Notification 组件会自动关闭，但是通过设置`duration`，可以控制关闭的时间间隔，特别的是，如果设置为`0`，则不会自动关闭。注意：`duration`接收一个`Number`，单位为毫秒，默认为`4500`。
```js
render() {
  return (
    <div>
      <Button plain={true} onClick={this.open.bind(this)}>可自动关闭</Button>
      <Button plain={true} onClick={this.open2.bind(this)}>不会自动关闭</Button>
    </div>
  )
}

open() {
  Notification({
    title: '标题名称',
    message: '这是提示文案这是提示文案这是提示文案这是提示文案这是提示文案这是提示文案这是提示文案这是提示文案'
  });
}

open2() {
  Notification({
    title: '提示',
    message: '这是一条不会自动关闭的消息',
    duration: 0
  });
}
```
:::

### 带有倾向性

带有 icon，常用来显示「成功、警告、消息、错误」类的系统消息

::: demo Element 为 Notification 组件准备了四种通知类型：`success`, `warning`, `info`, `error`。通过`type`字段来设置，除此以外的值将被忽略。同时，我们也为 Notification 的各种 type 注册了方法，可以在不传入`type`字段的情况下像`open5`和`open6`那样直接调用。
```js
render() {
  return (
    <div>
      <Button plain={true} onClick={this.open3.bind(this)}>成功</Button>
      <Button plain={true} onClick={this.open4.bind(this)}>警告</Button>
      <Button plain={true} onClick={this.open5.bind(this)}>消息</Button>
      <Button plain={true} onClick={this.open6.bind(this)}>错误</Button>
    </div>
  )
}

open3() {
  Notification({
    title: '成功',
    message: '这是一条成功的提示消息',
    type: 'success'
  });
}

open4() {
  Notification({
    title: '警告',
    message: '这是一条警告的提示消息',
    type: 'warning'
  });
}

open5() {
  Notification.info({
    title: '消息',
    message: '这是一条消息的提示消息'
  });
}

open6() {
  Notification.error({
    title: '错误',
    message: '这是一条错误的提示消息'
  });
}
```
:::

### 全局方法

Element 为 `Vue.prototype` 添加了全局方法 `$notify`。因此在 vue instance 中可以采用本页面中的方式调用 Notification。

### 单独引用

单独引入 Notification：

```javascript
import { Notification } from 'element-ui';
```

此时调用方法为 `Notification(options)`。我们也为每个 type 定义了各自的方法，如 `Notification.success(options)`。

### Options
| 参数      | 说明          | 类型      | 可选值                           | 默认值  |
|---------- |-------------- |---------- |--------------------------------  |-------- |
| title | 标题 | string | — | — |
| message | 说明文字 | string | — | — |
| type | 主题样式，如果不在可选值内将被忽略 | string | success/warning/info/error | — |
| duration | 显示时间, 毫秒。设为 0 则不会自动关闭 | number | — | 4500 |
| onClose | 关闭时的回调函数 | function | — | — |
