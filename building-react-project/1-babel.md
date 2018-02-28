# babel的配置
根目录下建立.babelrc文件

package.json中有babel选项，例如:"babel":{}
# .babelrc
主要组成由presets和plugins
```
{
  "presets":[],
  "plugins":[]
}
```
## presets
## plugins
## Vue项目中配置
```
{
  "presets": [
    "es2015",
    "stage-2"
  ],
  "plugins": [
    "transform-runtime"
  ],
  "comments": false
}
```
## React项目中的配置
```
{
  "presets": [
    [ "env", {"modules": false}],
    "stage-2",
    "react"
  ],
  "plugins": [
    "transform-runtime"
  ],
  "comments": false
}
```
