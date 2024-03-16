# CSS边框（border）属性详解

CSS边框属性允许你为HTML元素添加边框。边框是围绕在元素内容和内边距周围的线。你可以设置边框的样式、宽度和颜色。

### 边框样式（border-style）

`border-style` 属性定义了边框的样式。以下是可能的值：

- `none`：无边框。
- `hidden`：隐藏边框。
- `dotted`：点状边框。
- `dashed`：虚线边框。
- `solid`：实线边框。
- `double`：双线边框。
- `groove`：3D凹槽边框。
- `ridge`：3D垄状边框。
- `inset`：3D凹边边框。
- `outset`：3D凸边边框。

### 边框宽度（border-width）

`border-width` 属性定义了边框的宽度。你可以使用以下值：

- `thin`
- `medium`
- `thick`
- 具体的像素值，如 `1px`、`2px` 等

### 边框颜色（border-color）

`border-color` 属性定义了边框的颜色。你可以使用任何有效的CSS颜色值，如颜色名称、十六进制值、RGB值等。

### 简写属性

CSS提供了几个简写属性来同时设置多个边框属性：

- `border`：用于设置所有四个边框的样式、宽度和颜色。
- `border-top`、`border-right`、`border-bottom`、`border-left`：分别用于设置上、右、下、左四个边框的样式、宽度和颜色。


### 两者结合属性
由于边框的四边是可以独立设置CSS样式的，
所以上下左右都可以结合边框的宽度属性，边框的样式属性，边框的颜色属性进行单独设置
如`border-left-width`等，以此类推

### 表格总结

| 属性名 | 描述 | 可能的值 |
| --- | --- | --- |
| `border-style` | 定义边框的样式 | `none`, `hidden`, `dotted`, `dashed`, `solid`, `double`, `groove`, `ridge`, `inset`, `outset` |
| `border-width` | 定义边框的宽度 | `thin`, `medium`, `thick`, 具体像素值（如 `1px`、`2px` 等） |
| `border-color` | 定义边框的颜色 | 任何有效的CSS颜色值 |
| `border` | 简写属性，用于同时设置所有四个边框的样式、宽度和颜色 | 同上 |
| `border-top` | 简写属性，用于设置上边框的样式、宽度和颜色 | 同上 |
| `border-right` | 简写属性，用于设置右边框的样式、宽度和颜色 | 同上 |
| `border-bottom` | 简写属性，用于设置下边框的样式、宽度和颜色 | 同上 |
| `border-left` | 简写属性，用于设置左边框的样式、宽度和颜色 | 同上 |

注意：在使用简写属性时，属性的顺序是：`border-width`、`border-style`、`border-color`。如果省略了某个值，那么该值将使用其默认值。例如，`border: 2px solid;` 将设置边框宽度为2像素，样式为实线，颜色为默认颜色（通常是黑色）。