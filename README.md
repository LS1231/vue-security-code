# vue-security-code

> An security-code input implement by vue 2.0

![](https://img.shields.io/npm/dm/vue-security-code.svg)
![](https://img.shields.io/npm/v/vue-security-code.svg)

## Demo

[Live Demo >>](https://ls1231.github.io/vue-security-code/)

## Install

``` bash
npm i -S vue-security-code
```

## Usage
``` vue
<template>
    <security-code v-model="code"></security-code>
</template>

<script>
    import SecurityCode from 'vue-security-code'

    // Declare
    export default {
        components: { SecurityCode },
        data () {
          return {
            code: ''
          }
        }
    }
</script>
```

## Options

参数 | 说明 | 类型 | 可选值 | 默认值
---- | --- | --- | --- | ---
length | 长度 | number | — | 4
placeholder | 占位符 | string | — | -
theme | 主题 | string | block / line | block

## License

[MIT](https://github.com/LS1231/vue-security-code/blob/master/LICENSE) Copyright (c) 2017 liusong
