# Layout & 布局

协助进行页面级整体布局。

## 设计规则

### 尺寸

一级导航项偏左靠近 logo 放置，辅助菜单偏右放置。

- 顶部导航（大部分系统）：一级导航高度 64px，二级导航 48px。

- 顶部导航（展示类页面）：一级导航高度 80px，二级导航 56px。

- 顶部导航高度的范围计算公式为：48+8n。

- 侧边导航宽度的范围计算公式：200+8n。

### 交互

- 一级导航和末级的导航需要在可视化的层面被强调出来；

- 当前项应该在呈现上优先级最高；

- 当导航收起的时候，当前项的样式自动赋予给它的上一个层级；

- 左侧导航栏的收放交互同时支持手风琴和全展开的样式，根据业务的要求进行适当的选择。

## 组件概述

- `Layout`：布局容器，其下可嵌套 `Header` `Sider` `Content` `Footer` 或 `Layout` 本身，可以放在任何父容器中。

- `Header`：顶部布局，自带默认样式，其下可嵌套任何元素，只能放在 `Layout` 中。

- `Sider`：侧边栏，自带默认样式及基本功能，其下可嵌套任何元素，只能放在 `Layout` 中。

- `Content`：内容部分，自带默认样式，其下可嵌套任何元素，只能放在 `Layout` 中。

- `Footer`：底部布局，自带默认样式，其下可嵌套任何元素，只能放在 `Layout` 中。

### RA-Layout

RA 中，默认使用了 splitLayout 分列布局，启动后我们可以看到这样的界面。


 <img alt="split-layout" style="box-shadow: 0 3px 20px 0 rgba(189, 189, 189, 0.6);border-radius: 5px;margin: 30px 0;" src="./media/splitLayout.png">

</br>

对于标题和 logo，Layout 提供了 title和 logo属性来自定，如果你有更强的定制需求，可以试试编写 `components/Layout/SiteDetail.tsx` 文件。


### SettingDrawer

> 由于 SettingDrawer 过于灵活，并且通常业务不需要涉及如此广泛的场景变动，因此不建议在生产环境使用 SettingDrawer 的所有功能。

SettingDrawer 提供了一个图形界面来设置 layout 的配置，方便在演示环境中展示 Layout 的所有能力。

<img alt="settingDrawer" style="box-shadow: 0 3px 20px 0 rgba(189, 189, 189, 0.6);border-radius: 5px;margin: 30px 0;" src="./media/settingDrawer.png">


### 嵌套布局

在某些时候可能需要进行 layout 的嵌套，RA-Layout 提供了响应的变更入口。

<img alt="inlineLayout" style="box-shadow: 0 3px 20px 0 rgba(189, 189, 189, 0.6);border-radius: 5px;margin: 30px 0;" src="./media/inlineLayout.png">

</br>
</br>

调整方式，设置 layoutStatus 的 layoutMode 属性为 `inline` 即可。

```javascript

interface LayoutStatus extends StoreKeyValue {
  showSiderBar: boolean;
  showHeader: boolean;
  layoutMode: 'split' | 'inline';
  navigateMode: 'vertical' | 'horizontal';
  contentAreaWidthMode: 'max-width' | 'flow';
  fixSiderBar: boolean;
  fixHeader: boolean;
  visionTheme: 'light' | 'dark';
  collapsed: boolean;
  isMobile: boolean;
  currentColor: string;
}

@observable layoutStatus: LayoutStatus = {
  ...
  layoutMode: (layoutMode as 'split' | 'inline') || 'split', // 布局模式
  ...
};
```

### 顶部导航模式

通过设置 layoutStatus 的 navigateMode 属性为 `horizontal` 即可。

<img alt="topNavigator" style="box-shadow: 0 3px 20px 0 rgba(189, 189, 189, 0.6);border-radius: 5px;margin: 30px 0;" src="./media/topNavigator.png">

## 如何使用

在页面中引入 `BasicLayout` 组件即可，children将填充内容渲染区域。

```javascript
import BasicLayout from '@components/Layout/BasicLayout';

const MainSkeleton: React.FC = props => {
  return (
    <BasicLayout
      {...{
        isHorizontalNavigator: true
      }}
    >
      {<div>view</div>}
    </BasicLayout>
  );
};
export default MainSkeleton;
```
</br>

`BasicLayout` 支持参数

- isHorizontalNavigator `boolean` 

  使用顶部导航，默认为 `false`.

- siderBar `React.ReactNode`

  传入将替换RA基于路由表自动渲染的菜单，默认为空

- siteLogo `React.ReactNode`

  传入将替换项目logo区域，默认为空

- header `React.ReactNode`

  传入将替换header区域所有内容，默认为空

> 可参考 `src/skeleton/Main.tsx`