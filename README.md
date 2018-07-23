# vuetifyjs-webpack

> A Vue.js project

## Build Setup

``` bash
# install dependencies
yarn install

# serve with hot reload at localhost:8080
yarn run dev

# build for production with minification
yarn run build

# build for production and view the bundle analyzer report
yarn run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.gitcd ..hub.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).


# 使用

## 安装
```shell
$ yarn global add vue-cli
$ vue init vuetifyjs/webpack front-sample
  ? Project name front-sample
  ? Project description A Vue.js project
  ? Author shucheng@spacesystech.com
  ? Vue build standalone
  ? Install vue-router? Yes
  ? Use ESLint to lint your code? No
  ? Set up unit tests No
  ? Setup e2e tests with Nightwatch? No
  ? Use a-la-carte components? No
  ? Use custom theme? No
  ? Should we run `npm install` for you after the project has been created? (recommended) yarn
$ cd front-sample
$ yarn install
$ yarn run dev
```

## 修改conf/index.js
给dist增加相对路径
```javascript
build: {
  // Template for index.html
  index: path.resolve(__dirname, '../dist', 'vuetifyjs', 'index.html'),

  // Paths
  assetsRoot: path.resolve(__dirname, '../dist', 'vuetifyjs'),
  assetsSubDirectory: 'static',
  assetsPublicPath: '/vuetifyjs/'
}
```

## 修改build/dockerfile
```
RUN mkdir -p /app/www/vuetifyjs
ADD . /app/www/vuetifyjs
```

## 增加.drone.yml
.drone.yml

## 移除index.html中对googlefont的外部引用
```bash
# index.html
- <link href='https://fonts.googleapis.com/css?family=Roboto:300,400,500,700|Material+Icons' rel="stylesheet">

# src/assets
+ googlefonts.css
```

## yarn run build 
执行上面命令报npm version错误
```javascript
// ./build/check-versions.js
if (shell.which('yarn')) {
  versionRequirements.push({
    name: 'yarn',
    currentVersion: exec('yarn --version'),
    versionRequirement: packageConfig.engines.yarn
  })
}

// package.json
  "engines": {
    "node": ">= 6.0.0",
    "npm": ">= 3.0.0",
    "yarn": ">=1.5.0"
  },
```

# 如何取消登录
./build/dockerfile中对以下代码的注释
```dockerfile
FROM {{ BASEIMAGE }}
MAINTAINER {{ AUTHOR }}
LABEL Author={{ AUTHOR }} Name={{ PROJECT }} Version={{ VERSION }}
RUN mkdir -p /app/www/vuetifyjs
ADD ./dist /app/www/vuetifyjs
# ADD ./build/conf.json /etc/proxy/conf.json
```