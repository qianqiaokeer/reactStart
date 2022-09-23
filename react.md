# react 笔记
1. 初始化项目
   ````sh
   npm init
   ````
2. 使用JSX  Babel工具
   ````sh
   npm install babel-cli@6 babel-preset-react-app@3
   npx babel --watch src --out-dir . --presets react-app/prod 
   ````

## 工具链
+ package管理器
  
  yarn、npm
+ 打包器
  
  webpack 、parcel
+ 编译器
  
  babel
> 常见的工具链

### create react app
> 要求安装nodejs、和npm

> 创建项目
````sh
npx create-react-app my-app
cd my-app
npm start
````
> 部署生产环境

````sh
npm run build
````
### Next.js
### Gatsby
## JSX
> JSX表示对象

Babel 会把JSX转译成一个名为 