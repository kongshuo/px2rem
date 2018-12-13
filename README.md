<h2>在vue2.0中使用px2rem</h2>
<p>1.cnpm install lib-flexible --save-dev //flexible.js是淘宝出的弹性布局解决方式</p>	
<p>下载完成直接在入口文件main.js import 'lib-flexible'引入即可</p>	
<p>2.cnpm install postcss-loader --save-dev</p>
 <p>cnpm install px2rem-loader --save-dev</p>
<p>3.配置px2rem,在build文件中的utils.js中，代码如下</p>
<div>
 exports.cssLoaders = function (options) {
  options = options || {}

  const cssLoader = {
    loader: 'css-loader',
    options: {
      sourceMap: options.sourceMap
    }
  }

  const postcssLoader = {
    loader: 'postcss-loader',
    options: {
      sourceMap: options.sourceMap
    }
  }

  <a href="javascript:;">
 const px2remLoader = {
    loader: 'px2rem-loader',
    options: {
      remUnit: 75,//表示1rem = 75px
      baseDpr: 2
    }
  }</a>

  // generate loader string to be used with extract text plugin
  function generateLoaders (loader, loaderOptions) {
    const loaders = options.usePostCSS?
      <a href="javascript:;">[cssLoader, px2remLoader, postcssLoader]</a>
      : [cssLoader]
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
  <a href="javascript:;">postcss: [require('postcss-px2rem')()]</a>
}
  </div>
<p>5.cnpm run dev重启项目</p>
   

