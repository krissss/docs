## glob

[npm](https://www.npmjs.com/package/glob)

通过正则匹配文件

```js
function entries(globPath) {
  const files = glob.sync(globPath)
  const entries = {}
  for (let i = 0; i < files.length; i++) {
    const file = files[i]
    entries[path.basename(file, '.js')] = './' + file
  }
  return entries
}

const files = entries('src/entry/*.js')
```
