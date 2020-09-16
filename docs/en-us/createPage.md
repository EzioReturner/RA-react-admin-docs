# Create Page

Use RA directives to generate『page』。

## Create Class Component

According to the agreement of RA, we usually place the sub-page under the 'src/views' directory, by using the following code.

```bash
yarn raCreate -v exampleView
```

The following output will show in the console

```bash
...
yarn run v1.13.0
$ node scripts/tools.js -v exampleView
createType: ···exampleView··· created
✨  Done in 0.27s.
...
```

The ExampleView folder will automatically be generated containing `index.tsx` and `index.module.less` files in the 'src/views' directory, styles by default use `CSS Module`, can refer to [Style & Theme](/cssStyle)

</br>

<img alt="addview" style="box-shadow: 0 3px 20px 0 rgba(189, 189, 189, 0.6);border-radius: 5px;width:300px;" src="./media/addview.png">

</br>
</br>

`index.tsx`

```javascript
import React, { Component } from 'react'; 
import style from './index.module.less'; 

class ExampleView extends Component {
	render() {
		return <div>ExampleView now is work!</div>;
	}
}

export default ExampleView;
```


## Create Function Component

Add additional configuration `-fc` will be created as a functional component

```bash
yarn raCreate -v exampleFC -fc
```

```javascript
import React from 'react';
import style from './index.module.less';

interface ExampleFCProps {}

const ExampleFC: React.FC<ExampleFCProps> = props => {
  return <div>ExampleFC now is work!</div>;
};

export default ExampleFC;
```


## Create PageWrapper Hoc Component

Add additional configuration `-page` will be created an Hoc Component with PageWrapper

```bash
yarn raCreate -v examplePage -page
```

`examplePage.tsx`

```javascript
import React, { Component } from 'react'; 
import PageWrapper from '@components/PageWrapper'; 
import FormatterLocale from '@components/FormatterLocale'; 
import style from './index.module.less'; 

class examplePage extends Component { 
  render() {
    return <PageWrapper title={<FormatterLocale id="yourId" defaultMessage="examplePage" />}> 
      ExamplePage is at work!
    </PageWrapper>; 
  } 
} 

export default ExamplePage;
```

> After visit the page`s route [Router And Menu](/en-us/router), You can see the following page, A base page with a header, body, and breadcrumbs has been generated.

 <img alt="examplePage" style="box-shadow: 0 3px 20px 0 rgba(189, 189, 189, 0.6);border-radius: 5px;width:600px;" src="./media/examplePage.png">


## Create Common Component

Generate common component was similar to others, change `-v` to `-c`:

```bash
yarn raCreate -c exampleComponent
```

After the command is executed the file will be generated in `src/components`.

<!-- 
## PageWrapper组件

>上例中，我们引入了PageWrapper组件，该组件接收以下参数：

### hideBreadcrumb

- 类型： `boolean`

  控制是否显示面包屑

### title

- 类型： `string` 或者 `ReactDOM`

### subTitle

- 类型： `string` 或者 `ReactDOM`

### content

- 类型： `string` 或者 `ReactDOM`

### extraContent

- 类型： `string` 或者 `ReactDOM`

详细对应可参考下图，具体使用代码参考 `src/views/List/CardList.tsx` 文件。

<img alt="pageHeader" style="box-shadow: 0 3px 20px 0 rgba(189, 189, 189, 0.6);border-radius: 5px;width:600px;" src="./media/pageHeader.png"> -->