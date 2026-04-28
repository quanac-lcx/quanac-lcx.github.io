效果：[hiac.me](https://hiac.me)
```css
<script src="https://polyfill.alicdn.com/v3/polyfill.min.js?features=String.prototype.replaceAll"></script>

<!--评论系统使用的js-->
<script src="https://unpkg.com/valine/dist/Valine.min.js"></script>

<!-- Font6，自定义底部使用和看板娘使用的图标和字体文件-->
<link type="text/css" rel="stylesheet" href="https://npm.elemecdn.com/font6pro@6.3.0/css/fontawesome.min.css" media="all" />
<link href="https://npm.elemecdn.com/font6pro@6.3.0/css/all.min.css" rel="stylesheet" />


<style>
  /* 去除通知栏 右上角 X */
  .notify-render .hope-close-button {
    display: none;
  }
  /*底部*/
  .footer {
    color:white !important;
    /* display: none !important; */
  }

  /* 此选项两处CSS 在v3.31.0中已优化 滚动显示 和 右下角设置网格模式尺寸大小 */
  /* 文字超长自动换行 */
  /*.name-box .name {
    white-space: unset !important;
    overflow: unset !important;
    }*/
  /* 缩略图图片变大 代码中的160px 自己改 现在是注释状态若需要自行解除注释 */
  /*.obj-box > div {
    grid-template-columns: repeat(auto-fill, minmax(160px, 1fr))
    }
    .obj-box > div .item-thumbnail{
    height: 100px;
    }*/

  /*白天背景图*/
  .hope-ui-light {
    background-image: url("https://resources.cn-sy1.rains3.com/openlist/wallpaper_minecraft_java_edition_2058x1440.webp") !important;
    background-repeat: no-repeat;
    background-size: cover;
    background-attachment: fixed;
    background-position-x: center;
  }
  /*夜间背景图*/
  .hope-ui-dark {
    background-image: url("https://resources.cn-sy1.rains3.com/openlist/wallpaper_minecraft_java_edition_2058x1440.webp") !important;
    background-repeat: no-repeat;
    background-size: cover;
    background-attachment: fixed;
    background-position-x: center;
  }

  /*主列表白天模式透明*/
  .obj-box.hope-stack.hope-c-dhzjXW.hope-c-PJLV.hope-c-PJLV-igScBhH-css {
    background-color: rgba(255, 255, 255, 0.5) !important;
  }
  /*主列表夜间模式透明*/
  .obj-box.hope-stack.hope-c-dhzjXW.hope-c-PJLV.hope-c-PJLV-iigjoxS-css {
    background-color: rgb(0 0 0 / 50%) !important;
  }
  /*readme白天模式透明*/
  .hope-c-PJLV.hope-c-PJLV-ikSuVsl-css {
    background-color: rgba(255, 255, 255, 0.5) !important;
  }
  /*readme夜间模式透明*/
  .hope-c-PJLV.hope-c-PJLV-iiuDLME-css {
    background-color: rgb(0 0 0 / 50%) !important;
  }

  /*顶部右上角切换按钮透明*/
  .hope-ui-light .hope-c-ivMHWx-hZistB-cv.hope-icon-button {
    background-color: rgba(255, 255, 255, 0.5) !important;
  }
  .hope-ui-dark .hope-c-ivMHWx-hZistB-cv.hope-icon-button {
    background-color: rgb(0 0 0 / 50%) !important;
  }

  /*右下角侧边栏按钮透明 第一个是白天 第二个是夜间*/
  .hope-ui-light .hope-c-PJLV-ijgzmFG-css {
    background-color: rgba(255, 255, 255, 0.5) !important;
  }
  .hope-ui-dark .hope-c-PJLV-ijgzmFG-css {
    background-color: rgb(0 0 0 / 50%) !important;
  }
  /*白天模式代码块透明*/
  .hope-ui-light pre {
    background-color: rgba(255, 255, 255, 0.1) !important;
  }
  /*夜间模式代码块透明*/
  .hope-ui-dark pre {
    background-color: rgba(255, 255, 255, 0) !important;
  }

  /*左侧侧边栏目录*/
  /*白天模式*/
  .hope-ui-light .hope-c-PJLV-ieGWMbI-css {
    background: rgba(255, 255, 255, 0.5) !important;
  }
  /*夜间模式*/
  .hope-ui-dark .hope-c-PJLV-ieGWMbI-css {
    background-color: rgb(0 0 0 / 50%) !important;
  }
  /* 返回顶部 */
  .hope-c-PJLV-ihVEsOa-css {
    background: rgba(255, 255, 255, 0.5) !important;
  }
  .hope-ui-dark .hope-c-PJLV-ihVEsOa-css {
    background-color: rgb(0 0 0 / 50%) !important;
  }

  /*顶部*/
  #root > .header {
    background: rgba(255, 255, 255, 0);
  }
  /*导航条*/
  /*白天模式*/
  .hope-ui-light .body > .nav {
    background-color: rgba(255, 255, 255, 0.5);
    border-radius: var(--hope-radii-xl);
  }
  /*夜间模式*/
  .hope-ui-dark .body > .nav {
    background-color: rgb(0 0 0 / 50%);
    border-radius: var(--hope-radii-xl);
  }
  /*隐藏导航条遮罩*/
  .body > .nav::after {
    display: none;
  }

  /*底部CSS，.App .table这三个一起的*/
  dibu {
    border-top: 0px;
    position: absolute;
    bottom: 0;
    width: 100%;
    margin: 0px;
    padding: 0px;
  }
  .App {
    min-height: 85vh;
  }
  .table {
    margin: auto;
  }

  /*全局字体*/
  * {
    font-family: LXGW WenKai;
  }
  * {
    font-weight: bold;
  }
  body {
    font-family: LXGW WenKai;
  }

  /*渐变背景CSS*/
  #canvas-basic {
    position: fixed;
    display: block;
    width: 100%;
    height: 100%;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: -999;
  }
</style>
```
来源于互联网。