# Quick Start

> Before start, a good knowledge base of [React](https://reactjs.org/) 、 [ES2015+](http://es6.ruanyifeng.com/)、 [Mobx](https://mobx.js.org/)、  [Antd Design](https://ant.design/docs/react/introduce-cn), And properly installed and configured [Node.js](https://nodejs.org/en/) v10 or above 、[Git](https://git-scm.com/).It would be helpful if you have pre-existing knowledge on those.

## Installation

```bash
git clone https://github.com/EzioReturner/RATurbo-react-admin.git
cd RATurbo-react-admin
```

## Function modules

```bash
- layout
- navigator
- components
    - router
    - layout setting
    - transition hoc
    - async loader
    - loading 
    - i18n
- UI component
    - program
    - gallery
    - form page
    - list page
    - result page
    - exception page
- visual chart
- view
    - sign in
    - dashboard
- scalable & mobile support 
- base on TypeScript
```

## Scaffolding

The project layout is as follows:

```bash
├── build                   // Default build output directory
├── e2e                     // e2e test directory
├── node_modules            // Black hole
├── public                  // Static resource 
├── scripts                 // Program script directory
├── src                     // Source code
│    ├── api                // Backend Services
│    ├── assets             // Assets directory
│    ├── components         // Components directory
│    ├── config             // Application configuration
│    ├── layout             // Common Layouts
│    ├── locales            // i18n resources
│    ├── models             // Ts interface configuration
│    ├── store              // Mobx directory
│    ├── style              // Common Styles
│    ├── utlis              // Utility
│    ├── views              // Sub-pages and templates
│    └── index.tsx          // Entry
├── webpack                 // Webpack configuration
├── .babelrc.js             
├── .eslintrc.js          
├── .gitignore             
├── .prettierignore        
├── .yarnrc                
├── jest-puppeteer.config   
├── jest.config            
├── jest.setup.config      
├── package.json          
├── README.md               
├── tsconfig.json          
└── yarn-lock              
```

## Development
Yarn is recommended. If NPM installation is too slow, taobao image can be used.s

1.Install Dependencies.
```bash
yarn install
```

2.Start local server.
```bash
yarn start
```

After the startup is complete, open a browser and visit [http://localhost:9527](http://localhost:9527).

 <img alt="split-layout" style="box-shadow: 0 3px 20px 0 rgba(189, 189, 189, 0.6);border-radius: 5px;width:600px;" src="./media/splitLayout.png">

> If you need to change the startup port, you can configure it in the .env file.
