# ts-jest-demo

从 0 创建单元测试项目

[JEST 官方文档](https://jestjs.io/docs/getting-started#using-typescript)
[Yarn 官方文档](https://classic.yarnpkg.com/en/docs/usage)

初始化项目

```bash
yarn init -y
```

创建项目源码文件夹 src, 并创建入口文件 index.ts

创建测试代码文件夹 test,并创建测试文件 index.spec.ts

安装 typescript

```bash
yarn add typescript --dev
```

创建 ts.config 文件

```bash
npx tsc --init
```

安装单元测试库

```
yarn add jest @types/jest --dev
```

修改 tsconfig.json

```json
"types": ["Jest"] /*修改types中添加jest*/,
```

修改 package.json 文件

```json
"scripts": {
    "test": "jest"
},
```

在终端执行测试代码

```bash
yarn test
```

到这里基本就结束了,另外默认配置的情况下 jest 是在 node.js 环境下使用,想要使用 esm 需要使用到 babel，将代码进行转换.jest 官方给出了解决方案

```bash
yarn add --dev babel-jest @babel/core @babel/preset-env
```

创建 babel.config.js 并添加

```js
module.exports = {
	presets: [["@babel/preset-env", { targets: { node: "current" } }]]
}
```

到这步的操作是为了让 babel 能够根据我们当前的 node 版本进行转化，但是还没完

对 typescipt 的支持

```bash
yarn add --dev @babel/preset-typescript
```

babel.config.js 更改为

```js
module.exports = {
	presets: [["@babel/preset-env", { targets: { node: "current" } }]]
}
```

到此就算告一段落了， 后续根据自身项目的需求可以自行更改
