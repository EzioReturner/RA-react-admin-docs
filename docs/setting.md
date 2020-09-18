# 系统配置

RA提供了一系列自定义配置，可在 `/src/config/setting.js` 文件中自行定义:

## siteName

- 类型: `string`

  配置站点名称，应用到登录框，侧边栏顶部的标题文字显示以及 index.html 中的 `<title>` 标签

## copyright

- 类型: `string[]`

  配置版权声明，应用到登录页、布局底部，若不传则不显示footer

## menuLinkUrl

- 类型: `string`

  左侧菜单顶部点击的弹出窗口url地址

## iconfontUrl

- 类型: `string`

  iconfont 组件远端链接地址

## useMenu

- 类型: `boolean`

  控制是否显示菜单，包括顶部导航模式下的菜单

## useHeader

- 类型: `boolean`

  控制是否显示头部header，包括顶部导航模式下的头部header

## layoutMode

- 类型:  `string`: `splitLayout` | `inlineLayout` 

  替换 `fixedHeader` 字段，用于调整layout展示模式

## navigateMode

- 类型: `string`: `vertical` | `horizontal`

  控制导航风格

## contentAreaWidthMode

- 类型: `string`: `max-width` | `flow`

  内容区域宽度模式

## useSetting

- 类型: `boolean`

  是否启用系统设置面板 
  
> tips: 改变该配置需重启项目

## useSiteIcon

- 类型: `boolean`

  配置显示站点图标，图标路径默认为 `assets/image/logo.png`

## usei18n

- 类型: `boolean`

  启用国际化部分组件

## i18n

- 类型: `Object`

  配置国际化，默认配置如下:

  ```javascript
  i18n: {
    languages: [
      {
        key: 'zh',
        title: '简体中文',
        icon: '🇨🇳'
      },
      {
        key: 'en',
        title: 'English',
        icon: '🇬🇧'
      },
      {
        key: 'ja',
        title: '日本语',
        icon: '🇯🇵'
      }
    ],
    defaultLanguage: 'zh'
  }
  ```

  ### i18n.languages

  - 类型: `Array`

    指定应用支持哪些语言，每种语言的对象属性如下:

    - `key` - 用于区分语言，以及 `src/locals` 下对应的语言包文件

    - `title` - 语言名称，布局顶部语言切换显示

    - `icon` - 语言的国旗图标emoji，布局顶部语言切换显示

 ### i18n.defaultLanguage
   
   - 类型: `string`

        配置默认语言
