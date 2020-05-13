# 样式

## Less

RA使用 less 作为样式语言，建议在使用前或者遇到疑问时学习一下 [less](http://lesscss.cn/) 的相关特性。

### CSS Modules

在样式开发过程中，有两个问题比较突出：

`全局污染`，`选择器复杂` 为解决这两个问题，RA提供了CSS Modules 模块化方案，使用方法如下：

> 默认webpack只对 `.module.scss` 命名的文件解析为 css modules

```javascript
import styles from './style.module.less';

<div className={styles.title}>{title}</div>
```

在上面的样式中，.title只会在本文件生效。如果需要一个全局生效的样式，可以使用 `:global` 。

```css
/* 定义全局样式 */
:global(.text) {
  font-size: 16px;
}

/* 定义多个全局样式 */
:global {
  .footer {
    color: #ccc;
  }
  .sider {
    background: #ebebeb;
  }
}
```

## 系统样式

我们参考 Ant Design 视觉风格，并在其基础之上对部分样式进行了调整，如果对视觉风格有额外的要求，推荐使用以下的方式进行定制。

## Antd样式覆盖

我们在 `src/styles/antdStyle.less` 中对部分 `antd` 的样式进行了重写，使其更贴近RA的整体风格，如需调整可在该文件中修改。

> tips: 文件中包含大量覆盖动态主题的样式代码，移除后将影响动态主题切换效果。

## RA样式

RA中提供了一套全局生效的css样式。可在 `src/styles/mainVars.less` 中找到，例如：

- 颜色值

```css
...
@success-color: #00ce68;
@error-color: #e65251;
@warning-color: #ffaf00;
@processing-color: #308ee0;
...
```

- 边距 字体 对齐方式

```css
...
@spacing-mini: 4px;
@spacing-small: 8px;
@spacing-normal: 12px;
@spacing-middle: 16px;
@spacing-large: 24px;
@spacing-huge: 36px;
...
```

> 值得注意的是：RA利用了 `sass-resources-loader`[![](/media/link.svg)](https://github.com/shakacode/sass-resources-loader) 插件，全局注入 `mainVars.less` 与 `customClass.less` 中声明的样式。
