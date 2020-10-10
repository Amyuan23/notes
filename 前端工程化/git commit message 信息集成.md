# Git Commit Message集成实践

本篇文章是对【[优雅的提交你的 Git Commit Message](https://juejin.im/post/5afc5242f265da0b7f44bee4#heading-9)】的实践总结

用于保障项目 commit message 的规范和格式化

好的习惯，受益终身

## 格式

可以看看[angular提交记录](https://github.com/angular/angular.js/commits/master)

> 示例:
> chore(docs.angularjs.org): upgrade Firebase libraries
> 类型（修改的文件）：改了啥


一般来说，需要对我们的提交内容进行以下几种类型的划分，从而使得每次的代码变更都十分清晰。

- feat: 新特性

- fix: 修改问题

- refactor: 代码重构

- docs: 文档修改

- style: 代码格式修改, 注意不是 css 修改

- test: 测试用例修改

- chore: 其他修改, 比如构建流程, 依赖管理.

- scope: commit 影响的范围, 比如: route, component, utils, build...

  

## 使用工具 自动生成指定的格式

自己写提交信息，很有可能在空格、拼写、顺序等方面出现不统一

从工程化角度来说，使用工具，规范我们的每一次提交是有必要的



这里，我们使用 [commitizen/cz-cli](https://github.com/commitizen/cz-cli) ：

### 全局安装

```sh
npm install commitizen -g
```

adapter安装，可以理解为一个commit 规范预设 preset

```sh
npm install -g cz-conventional-changelog
echo '{ "path": "cz-conventional-changelog" }' > ~/.czrc
```

### 项目级安装

```sh
npm install -D commitizen cz-conventional-changelog
```

package.json中配置:

```json
"script": {
    ...,
    "commit": "git-cz",
},
 "config": {
    "commitizen": {
      "path": "node_modules/cz-conventional-changelog"
    }
  }
```

### adapter部分 自定义安装

 [cz-customizable](https://link.zhihu.com/?target=https%3A//github.com/leonardoanalista/cz-customizable)是自定义的adapter库

全局 或 项目级别安装:

```sh
npm i -g cz-customizable
# or
npm i -D cz-customizable
```

修改 .czrc 或 package.json 中的 config 为:

```json
{ "path": "cz-customizable" }
or
  "config": {
    "commitizen": {
      "path": "node_modules/cz-customizable"
    }
  }
```

同时在~/ 或项目目录下创建 .cz-config.js 文件, 维护你想要的格式
```powershell
vim ~/.cz-config.js 
```

例如输入一下内容

```js
'use strict';

module.exports = {

  types: [
    {
      value: 'WIP',
      name : '💪  WIP:      Work in progress'
    },
    {
      value: 'feat',
      name : '✨  feat:     A new feature'
    },
    {
      value: 'fix',
      name : '🐞  fix:      A bug fix'
    },
    {
      value: 'refactor',
      name : '🛠  refactor: A code change that neither fixes a bug nor adds a feature'
    },
    {
      value: 'docs',
      name : '📚  docs:     Documentation only changes'
    },
    {
      value: 'test',
      name : '🏁  test:     Add missing tests or correcting existing tests'
    },
    {
      value: 'chore',
      name : '🗯  chore:    Changes that don\'t modify src or test files. Such as updating build tasks, package manager'
    },
    {
      value: 'style',
      name : '💅  style:    Code Style, Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)'
    },
    {
      value: 'revert',
      name : '⏪  revert:   Revert to a commit'
    }
  ],

  scopes: [],

  allowCustomScopes: true,
  allowBreakingChanges: ["feat", "fix"]
};
```

### 用法

```sh
git cz
```



## [commitlint](https://github.com/conventional-changelog/commitlint) :校验是否符合规范

`git cz`只是为提交代码增添一种方式，我们仍可以用`git commit`提交代码。

这样一来，仍然无法避免提交不规范的信息。

因此，需要当我们提交的不符合规范的信息时, 直接拒绝提交。



这里，我们使用[commitlint](https://github.com/conventional-changelog/commitlint)来校验提交信息

安装：

```powershell
npm install --save-dev @commitlint/cli
```

```powershell
npm i --save-dev @commitlint/config-conventional

# Configure commitlint to use conventional config
echo "module.exports = {extends: ['@commitlint/config-conventional']}" > commitlint.config.js
```

package.json

```json
{
  "husky": {
    "hooks": {
      "commit-msg": "commitlint -E HUSKY_GIT_PARAMS"
    }
  }
}
```

[husky安装](https://github.com/typicode/husky)

