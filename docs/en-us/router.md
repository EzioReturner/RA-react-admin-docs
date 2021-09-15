# Router & Menu

For easy management, routes in RA are centrally configured and managed in `router.config.tsx`.

## Operation Module

RA implements the following modules through components in the framework:
- `Route Management` configures routes information in `router.config.tsx` according to the agreed syntax.
- `Menu rendering` menu component 'navigator.tsx' generates menus based on routing information by `router.config.tsx`.
- `Breadcrumb` in `PageHeader` component built-in association routing.

### Router

Routes in RA are managed through `router.config.tsx`. We provide the following parameters to aid in generating the menu. Its implementation in `components/RenderRoutes` 。

- `name` 对应生成菜单项的文本
- `icon` 对应菜单的图标，支持iconfont，请以string类型传入，并在setting中配置您的iconfont地址，或传入svg。
- `hideMenu` 可以在列表中不显示这个菜单项，包括底下的子路由。
- `authority` 用于配置路由的权限。如果配置了该项那么权限组件 [Authority](/authority) 会对当前用户权限进行验证，并决定是否展示。
- `loading` 用于异步加载过载时间过长时开启loading遮罩。
- `component` 用于表述路由对应的模块信息，为一个两位的数组，
  * `component[0]` 表示模块的路径或者模块本身，如果使用路径则默认为懒加载模式
  * `component[1]` 表示模块进入时的动画效果，如果不传默认为 `slide` 样式，详见：[过渡效果](/transition)


> 余下配置项请参考 `src/model/index.ts` 文件

路由配置数据格式如下：

```javascript
{
  name: 'program',
  icon: 'appstore',
  path: '/program',
  routes: [
    {
      name: 'analysis',
      path: '/program/analysis',
      component: ['/views/Program/Analysis'],
      authority: ['admin']
    }
  ]
}
```

###  菜单

菜单会根据 `router.config.tsx` 自动生成，具体实现在 `components/Layout/SiderMenu.tsx`。

> 如果你的项目不需要菜单，你可以在 [系统配置](/setting) 中设置 `useMenu` 为 `false`

#### 从服务器请求菜单

只需在 `store/layoutStore.ts` 中发起请求，将返回数据处理成类似格式即可。

```javascript
...
获取异步菜单信息
setMenu(menu);
...

// 动态设置路由方法
@action setMenu(menu: Array<RouteRoot>): void {
  this.routeConfig = menu;
}
```

### 面包屑

面包屑由 `PageHeader/Breadcrumb.jsx` 组件实现。挂载 `PageWrapper` 的组件将自动添加面包屑，面包屑不需要传入参数，面包屑的数据通过 `layoutStore` 的 `breadcrumbList` 提供。

`breadcrumbList` 数据格式如下：

```javascript
{
  display: true
  name: "cardList"
  path: "/list/cardList"
}
```

> 如需要单独使用面包屑组件，在页面中挂载 `Breadcrumb` 组件即可。