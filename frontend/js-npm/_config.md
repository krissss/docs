## dotenv

[npm](https://www.npmjs.com/package/dotenv)

将 .env 放到 process.env

```js
require('dotenv').config()

console.log(process.env.DB_HOST)
```

## dotenv-webpack

[npm](https://www.npmjs.com/package/dotenv-webpack)

webpack plugin, 允许被 webpack 编译的 js 中使用 `procee.env.NAME` 的形式获取参数

```js
const Dotenv = require('dotenv-webpack')

// webpack.config.js
module.exports = {
  ...
  plugins: [
    new Dotenv()
  ]
  ...
};

// some js
console.log(process.env.DB_HOST)
```

注意：不同于 [dotenv](#dotenv)，dotenv-webpack 会将 `process.env.DB_HOST` 编译成对应的值，并不是实时获取，因此修改 .env 后需要重新编译
