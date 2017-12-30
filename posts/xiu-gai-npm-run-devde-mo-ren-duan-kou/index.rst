.. title: 修改npm run dev的默认端口
.. slug: xiu-gai-npm-run-devde-mo-ren-duan-kou
.. date: 2017-12-30 18:10:22 UTC+08:00
.. tags: npm, vuejs
.. category: javascript
.. link: 
.. description: 
.. type: text


修改项目目录中的 **config/index.js**

.. code-block :: javascript
    :linenos:

    // see http://vuejs-templates.github.io/webpack for documentation.
    var path = require('path')

    module.exports = {
        build: {
            env: require('./prod.env'),
            index: path.resolve(__dirname, '../dist/index.html'),
            assetsRoot: path.resolve(__dirname, '../dist'),
            assetsSubDirectory: 'static',
            assetsPublicPath: '/',
            productionSourceMap: true,
            // Gzip off by default as many popular static hosts such as
            // Surge or Netlify already gzip all static assets for you.
            // Before setting to `true`, make sure to:
            // npm install --save-dev compression-webpack-plugin
            productionGzip: false,
            productionGzipExtensions: ['js', 'css'],
            // Run the build command with an extra argument to
            // View the bundle analyzer report after build finishes:
            // `npm run build --report`
            // Set to `true` or `false` to always turn it on or off
            bundleAnalyzerReport: process.env.npm_config_report
        },
        dev: {
            env: require('./dev.env'),
            port: 8080,
            autoOpenBrowser: true,
            assetsSubDirectory: 'static',
            assetsPublicPath: '/',
            proxyTable: {},
            // CSS Sourcemaps off by default because relative paths are "buggy"
            // with this option, according to the CSS-Loader README
            // (https://github.com/webpack/css-loader#sourcemaps)
            // In our experience, they generally work as expected,
            // just be aware of this issue when enabling this option.
            cssSourceMap: false
        }
    }


修改里面的port即可。
