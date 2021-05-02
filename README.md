安装Gridsome CLI

```
yarn global add @gridsome/cli
```

安装node-gyp

```
npm install -g node-gyp
```

创建项目

```
gridsome create my-gridsome-site
```

删除node_modules

安装依赖

```
cnpm install
```

运行

```
gridsome develop
```

预览

```
http://localhost:8081/
```

安装tailwindcss

```
cnpm install tailwindcss
```

安装PostCSS-PurgeCSS

```
cnpm i -D @fullhuman/postcss-purgecss
```

src/main.css

```
@tailwind base;

@tailwind components;

@tailwind utilities;
```

src/main.js

```
// This is the main.js file. Import global CSS and scripts here.
// The Client API can be used here. Learn more: gridsome.org/docs/client-api
require('~/main.css')
import DefaultLayout from '~/layouts/Default.vue'

export default function (Vue, { router, head, isClient }) {
  // Set default layout as a global component
  Vue.component('Layout', DefaultLayout)
}

```

新建tailwind配置文件

```
npx tailwind init
```

tailwind.config.js

```
module.exports = {
    theme: {
        extend: {}
    },
    variants: {},
    plugins: []
}
```

gridsome.config.js

```
const tailwind = require('tailwindcss')
const purgecss = require('@fullhuman/postcss-purgecss')

const postcssPlugins = [
  tailwind(),
]

if (process.env.NODE_ENV === 'production') postcssPlugins.push(purgecss(require('./purgecss.config.js')))

module.exports = {
    siteName: 'Gridsome',
    plugins: [],
    css: {
        loaderOptions: {
            postcss: {
                plugins: postcssPlugins,
            },
        },
    },
}
```

purgecss.config.js

```
module.exports = {
    content: [
        './src/**/*.vue',
        './src/**/*.js',
        './src/**/*.jsx',
        './src/**/*.html',
        './src/**/*.pug',
        './src/**/*.md',
    ],
    whitelist: [
        'body',
        'html',
        'img',
        'a',
        'g-image',
        'g-image--lazy',
        'g-image--loaded',
    ],
    extractors: [
        {
            extractor: content => content.match(/[A-z0-9-:\\/]+/g),
            extensions: ['vue', 'js', 'jsx', 'md', 'html', 'pug'],
        },
    ],
}
```

删除node_modules

安装依赖

```
cnpm install
```

运行

```
gridsome develop
```

