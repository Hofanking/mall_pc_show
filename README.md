# 安装

```
npm install
```

# 运行

```
npm run serve
```

# 生成 dist

```
npm run build
```

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

# 2. 路由跳转

## 2.1 指定路由显示

可以在配置路由时，添加【meta】属性

```js
{
  path: '/home',
  component: Home,
  meta: { show: true }, // 是否显示Footer组件
}
```

可以在组件中，使用$route 获取到

```html
<footer v-show="$route.meta.show"></footer>
```

## 2.2 路由传参方式

### 2.2.1 字符串形式

```js
this.$router.push(
  '/search/' + this.keyword + '?k=' + this.keyword.toUpperCase()
)
```

### 2.2.2 模板字符串

```js
this.$router.push(`/search/${this.keyword}?k=${this.keyword.toUpperCase()}`)
```

### 2.2.3 对象

此种方式要给路由配置 name 属性

```js
this.$router.push({
  name: 'searcg',
  params: { keyword: this.keyword },
  query: { k: this.keyword.toUpperCase() },
})
```

## 2.2.4 路由参数获取

```js
params 参数：$route.params.keyword
query参数：$route.query.k
```
