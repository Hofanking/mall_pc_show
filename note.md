# 1. 脚手架下载下来的项目稍微配置一下

## 1.1 开启浏览器自动打开

在 package.json 文件中：

```json
        "scripts": {
         "serve": "vue-cli-service serve --open", // --open参数开启浏览器自动打开
          "build": "vue-cli-service build",
          "lint": "vue-cli-service lint"
        },
```

## 1.2 关闭 eslint 校验工具

在项目根目录下，创建 vue.config.js 文件，对外暴露

```js
module.exports = {
  lintOnSave: false, // 关闭eslint校验
}
```

## 1.3 src 文件夹的别名的设置

因为项目大的时候 src（源代码文件夹）里面目录会很多，找文件不方便，设置 src 文件夹的别名的好处，找文件会方便一些，在项目根目录下创建 jsconfig.json 文件。
src 文件夹简写方法，配置别名。【@代表的是 src 文件夹，这样将来文件过多，找的时候方便很多】

```json
{
  "compilerOptions": {
    "baseUrl": "./",
    "paths": {
      "@/_": ["src/_"] // 以后在项目中，使用@符号，就是从src下查找文件
    }
  },
  "exclude": ["node_modules", "dist"] // 除了在node_modules和dist目录下
}
```
