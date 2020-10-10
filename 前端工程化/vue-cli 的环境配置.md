

# vue-cli 的环境配置

环境文件：

```sh
.env                # 在所有的环境中被载入
.env.[mode]         # 只在指定的模式中被载入

.env.local          # 在所有的环境中被载入，但会被 git 忽略
.env.[mode].local   # 只在指定的模式中被载入，但会被 git 忽略
```

指定模式：

```
一般会指定这三种
.env.development
.env.production
.env.test
```


```json

"scripts": {

		"serve": "vue-cli-service serve", // 默认加载development模式，自动加载 .env.development 文件构建应用

    "build": "vue-cli-service build", // 默认加载production模式，自动加载 .env.production 文件构建应用

    "test": "vue-cli-service serve --mode test", // 加载test模式，加载 .env.test 文件构建应用

    "lint": "vue-cli-service lint"

  }

```



例子：以staging模式为例

`.env.staging` 文件：

```
NODE_ENV=production
VUE_APP_TITLE=My App (staging)
```

`vue-cli-service build --mode staging` 会在 staging 模式下加载可能存在的 `.env`、`.env.staging` 和 `.env.staging.local` 文件，然后根据 `NODE_ENV`配置构建出 **生产环境** 应用。