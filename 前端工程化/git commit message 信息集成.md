# Commit Message集成实践

[优雅的提交你的 Git Commit Message](https://juejin.im/post/5afc5242f265da0b7f44bee4#heading-9)

## 格式

- type: commit 的类型

- feat: 新特性

- fix: 修改问题

- refactor: 代码重构

- docs: 文档修改

- style: 代码格式修改, 注意不是 css 修改

- test: 测试用例修改

- chore: 其他修改, 比如构建流程, 依赖管理.

- scope: commit 影响的范围, 比如: route, component, utils, build...

- subject: commit 的概述, 建议符合  [50/72 formatting](https://link.zhihu.com/?target=https%3A//stackoverflow.com/questions/2290016/git-commit-messages-50-72-formatting)

- body: commit 具体修改内容, 可以分为多行, 建议符合 [50/72 formatting](https://link.zhihu.com/?target=https%3A//stackoverflow.com/questions/2290016/git-commit-messages-50-72-formatting)

- footer: 一些备注, 通常是 BREAKING CHANGE 或修复的 bug 的链接.



## Commitizen: 使用工具自动生成指定的格式

[commitizen/cz-cli](https://github.com/commitizen/cz-cli)

### 全局安装

```
npm install commitizen -g
```

adapter安装，可以理解为一个commit 规范预设 preset

```
npm install -g cz-conventional-changelog
echo '{ "path": "cz-conventional-changelog" }' > ~/.czrc
```

### 项目级安装

```
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

```
npm i -g cz-customizable
or
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
```
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

```
git cz
```



## [commitlint](https://github.com/conventional-changelog/commitlint) :校验是否符合规范

如果我们提交的不符合指向的规范, 直接拒绝提交，需要配置[commitlint](https://github.com/conventional-changelog/commitlint)

```
npm install --save-dev @commitlint/cli
```

```
npm i --save-dev @commitlint/config-conventional

# Configure commitlint to use conventional config
echo "module.exports = {extends: ['@commitlint/config-conventional']}" > commitlint.config.js
```

package.json

```
{
  "husky": {
    "hooks": {
      "commit-msg": "commitlint -E HUSKY_GIT_PARAMS"
    }
  }
}
```

[husky安装](https://github.com/typicode/husky)

