# 01 - Node, Yarn, 和 `package.json`

代码请点击 [这里](https://github.com/verekia/js-stack-walkthrough/tree/master/01-node-yarn-package-json).

在这部分，我们将安装Node，Yarn，`package.json` 文件, 打成一个包.

## Node

> 💡 **[Node.js](https://nodejs.org/)** 是JavaScript的运行环境，多用于后台开发，也用于通用脚本。在前端环境，它可以执行一系列任务，如 linting, 测试, 和配置文件。

本教程里我们将使用node作为基础，所以需要安装。前往**macOS** 或者 **Windows**对应的[下载 页面](https://nodejs.org/en/download/current/) , 或者Linux发行版的[包管理配置页面](https://nodejs.org/en/download/package-manager/)，进行安装。

比如，在**Ubuntu / Debian**, 您可运行以下命令来安装Node:

```sh
curl -sL https://deb.nodesource.com/setup_7.x | sudo -E bash -
sudo apt-get install -y nodejs
```

Node版本需要 > 6.5.0.

## NVM

当Node安装好后, 如果您想要更高的灵活性, 下载 ([Node 版本管理](https://github.com/creationix/nvm)), 安装NVM，使用最新的Node版本。

## NPM

NPM 是默认的Node包管理器，跟Node一起自动下载。包管理器用于下载管理包（您或者其他人写的代码模块）。在本教程里我们会使用到大量的包，所以我么可使用Yarn，另一种包管理器。

## Yarn

> 💡 **[Yarn](https://yarnpkg.com/)**作为Node.js的包管理器，比NPM更快，能离线缓存，在包的管理上[更可靠](https://yarnpkg.com/en/docs/yarn-lock)。

在2016年10月份 [发布](https://code.facebook.com/posts/1840075619545360)后, 它获得了广泛的应用，并且很快地成为JavaScript社区的包管理的选择。如果您想使用NPM，您可以用`npm install --save` 和 `npm install --save-dev`取代所有的`yarn add` 和 `yarn add --dev` 命令行 。

通过 [该说明](https://yarnpkg.com/en/docs/install) 在您的系统安装Yarn。如果您是MacOS或者Unix，建议使用*Alternatives*选项卡的的**安装脚本** , 以 [避免](https://github.com/yarnpkg/yarn/issues/1505) 安装其他包管理器:

```sh
curl -o- -L https://yarnpkg.com/install.sh | bash
```

## `package.json`

> 💡 **[package.json](https://yarnpkg.com/en/docs/package-json)** 是用于描述和统计您的JavaScript项目的文件。它包含了通用信息（项目名称，版本，贡献者以及批准等），工具信息，甚至运行*任务*的内容。 

- 新建一个文件夹, `cd` 进入。
- 运行`yarn init` ，回答问题`yarn init -y` 跳过所有问题), 自动生成一份 `package.json` 文件。

这里是一份本教程里使用的`package.json`基础文件:

```json
{
  "name": "your-project",
  "version": "1.0.0",
  "license": "MIT"
}
```

## Hello World

- 创建 `index.js` 文件，还有 `console.log('Hello world')`

🏁 此文件夹下运行 `node .` (`index.js` 是该文件夹Node查找文件). 它将会输出 "Hello world"。

**注释**: 看到 🏁 旗的标志了么? 每次到达检查点时，我都会使用它。有时一行会进行大量更改，您的代码可能无法工作，直到到达下一个检查点。

## `start` 脚本

运行 `node .`来执行我们的项目有写低层。取而代之，用NPM/Yarn触发代码执行。即使我们的代码更加复杂，使用 `yarn start`也能运行整个程序。

- 在 `package.json`里, 添加 `scripts`字段，如下:

```json
{
  "name": "your-project",
  "version": "1.0.0",
  "license": "MIT",
  "scripts": {
    "start": "node ."
  }
}
```

`start` 是我们给即将运行项目的任务起的名字。我们将在`scripts` 创建不同的任务。其他同级任务的名字为`stop` 和 `test`。

`package.json` 必须是有效的json文件,意味着不能以逗号结尾。所以当编写`package.json` 文件要当心。

🏁 运行 `yarn start`. 它将输出 `Hello world`.

## Git 和 `.gitignore`

-  `git init`初始化git仓库

- 创建 `.gitignore` 文件和添加内容如下:

```gitignore
.DS_Store
/*.log
```

`.DS_Store` 是在MacOs自动生成的文件，在您的仓库是没有的。

`npm-debug.log`和 `yarn-error.log` 是当你的包管理器遇到错误生成的，我们在仓库里并不像要。

## 安装使用package

在这部分，我们将安装和使用包。每个“package”是别人写的一段代码，你可以使用自己的代码。它可以是任何东西，我们将尝试使用帮你处理颜色的包。

-  通过运行 `yarn add color` 安装 `color`的包

打开 `package.json` ，可以看到 `color` 已经自动加入到 `dependencies`了。

目录中多了一个`node_modules` 文件夹，来存储包。

- 添加 `node_modules/` 到你的 `.gitignore`

你会注意到yarn生成`yarn.lock` 文件. 你应该将它提交到你的仓库，保证你的团队用的都是同一个版本的包。如果你使用NPM，*shrinkwrap*代表同样的文件。

- 将以下的内容写入`index.js`文件:

```js
const color = require('color')

const redHexa = color({ r: 255, g: 0, b: 0 }).hex()

console.log(redHexa)
```

🏁 运行 `yarn start`. 它将输出 `#FF0000`.

恭喜你！你已经安装使用了包。

`color` 只是教你如何使用包。 现在我们不再需要它了，可以进行卸载:

- 运行`yarn remove color`

## 两种类型的依赖

有两种不同类型的包依赖： `"dependencies"` 和 `"devDependencies"`:

**Dependencies** 是你的功能应用（React, Redux, Lodash, jQuery等）的需要包。可通过`yarn add [package]`来安装。

**Dev Dependencies**是用在开发期间或者构建你的应用（Webpack, SASS, linters, testing frameworks等）的包。 你可以通过 `yarn add --dev [package]`来安装。

下一章: [02 - Babel, ES6, ESLint, Flow, Jest, Husky](02-babel-es6-eslint-flow-jest-husky.md#readme)

回到 [目录](https://github.com/verekia/js-stack-from-scratch#table-of-contents)。
