## anser

[npm](https://www.npmjs.com/package/anser)

将 ansi 内容转化，转化成漂亮的 console 输出内容


## commander

[commander](https://www.npmjs.com/package/commander)

完整的 nodejs 命令行模式

## console-stamp

[console-stamp](https://www.npmjs.com/package/console-stamp)

cli 模式下日志输出（带时间、类型）

```js
require('console-stamp')(console, {
  format: ':date(yyyy-mm-dd HH:MM:ss.l):label'
});

console.log('xxx')
```

## chalk

[chalk](https://www.npmjs.com/package/chalk)

cli 模式下的输出带颜色

```js
// log.js

import chalk from 'chalk'

export default {
  debug(msg) {
    console.debug(this._colorMsg(msg))
  },
  info(msg) {
    console.info(this._colorMsg(msg, 'blue'))
  },
  warn(msg) {
    console.warn(this._colorMsg(msg, 'yellow'))
  },
  error(msg) {
    console.error(this._colorMsg(msg, 'red'))
  },
  success(msg) {
    console.log(this._colorMsg(msg, 'green'))
  },

  _colorMsg(msg, color = 'white') {
    if (typeof msg === 'string') {
      return chalk[color](msg)
    }
    return msg
  }
}
```