Vue.js 的过渡效果是指在 Vue 实例中的数据发生变化时，通过 CSS 过渡效果平滑地改变 DOM 的显示状态。Vue 提供了一系列的内置过渡效果，包括 `v-if`、`v-else-if`、`v-else`、`v-show` 和组件过渡。
过渡效果主要依赖于 Vue 的 `<transition>` 和 `<transition-group>` 元素，它们可以包裹任何元素或组件，为其添加进入和离开的过渡效果。
### 使用 `<transition>` 元素
`<transition>` 元素是 Vue 提供的一个包裹元素，它可以将任何元素包裹在内，并为其添加过渡效果。`<transition>` 元素可以指定进入和离开的过渡效果，例如：
```html
<transition name="fade">
  <div v-if="show">hello</div>
</transition>
```
在这个例子中，当 `show` 变量的值从 `false` 变为 `true` 时，`<div>` 元素将会以淡入效果显示；当 `show` 的值从 `true` 变为 `false` 时，`<div>` 元素将会以淡出效果隐藏。
`<transition>` 元素支持以下属性：
- `name`：指定过渡效果的名称，该名称对应 CSS 中的类名，用于定义过渡效果。
- `enter-class`/`leave-class`：进入/离开时的 CSS 类名。
- `enter-to-class`/`leave-to-class`：进入完成/离开完成时的 CSS 类名。
- `enter-active-class`/`leave-active-class`：进入/离开时的激活 CSS 类名，可以包含多个类名，用于激活特定的 CSS 属性，如 `transition`、`animation` 等。
- `mode`：指定过渡模式，可选值有 `in-out`、`out-in` 等。
### 使用 `<transition-group>` 元素
`<transition-group>` 元素用于有顺序的过渡，常用于列表的项的增删改查。它的工作方式类似于 `<transition>`，但是它会将所有子元素作为一个整体进行过渡。
```html
<transition-group name="list" tag="ul">
  <li v-for="item in items" :key="item.id">
    {{ item.text }}
  </li>
</transition-group>
```
在这个例子中，列表项（`<li>`）会在列表重新排序时以动画形式出现或消失。
`<transition-group>` 元素支持的属性与 `<transition>` 类似，但是它还有一些额外的属性，如 `move-class`，用于指定移动时的 CSS 类名。
### 自定义过渡效果
除了使用内置的过渡效果，你还可以通过自定义 CSS 类来定义过渡效果。例如，你可以创建一个名为 `bounce` 的过渡效果：
```css
.bounce-enter-active {
  animation: bounce-in .5s;
}
.bounce-leave-active {
  animation: bounce-out .5s;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}
@keyframes bounce-out {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(0);
  }
}
```
然后在 `<transition>` 元素中使用 `name` 属性指定这个过渡效果：
```html
<transition name="bounce">
  <div v-if="show">Bounce!</div>
</transition>
```
通过这种方式，你可以创建各种复杂的过渡效果。
总之，Vue 的过渡效果是一种强大的特性，它可以帮助你创建流畅的用户界面动画，提升用户体验。