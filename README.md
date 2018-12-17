<h2>在vue2.0中使用px2rem（一种px和rem自动转换的插件）</h2>
<p>1.cnpm install lib-flexible --save-dev //flexible.js是淘宝出的弹性布局解决方式</p>	
<p>下载完成直接在入口文件main.js import 'lib-flexible'引入即可</p>	
<p>2.cnpm install postcss-loader --save-dev</p>
 <p>cnpm install px2rem-loader --save-dev</p>
<p>3.配置px2rem,在build文件中的utils.js中，代码如下</p>
<div>
 代码：
 exports.cssLoaders = function (options) {
  options = options || {}
 在此添加
 <p>
 <span style="color:blue;">
  const px2remLoader = {
    loader: 'px2rem-loader',
    options: {
      remUnit: 75,//表示1rem = 75px
      baseDpr: 2
    }
  }
 </span>
 </p>
 <p>
  function generateLoaders (loader, loaderOptions) {
    const loaders = options.usePostCSS?
      [cssLoader, 添加： <span style="color:blue;">px2remLoader </span>, postcssLoader]
      : [cssLoader]
  </p>
    </div>
<p>4.在vue-loader中，代码如下</p>
<div>
 module.exports = {
  loaders: utils.cssLoaders({
    sourceMap: sourceMapEnabled,
    extract: isProduction
  }),
  cssSourceMap: sourceMapEnabled,
  cacheBusting: config.dev.cacheBusting,
  transformToRequire: {
    video: ['src', 'poster'],
    source: 'src',
    img: 'src',
    image: 'xlink:href'
  },
  添加：<p><span style="color:blue;">postcss: [require('postcss-px2rem')()]</span></p>
}
  </div>
<p>5.cnpm run dev重启项目</p>
   

