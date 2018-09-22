<template>
  <div id="app">
    <!-- :code="currentStyle"动态赋值code -->
    <StyleEditor ref="styleEditor" :code="currentStyle"></StyleEditor>
    <ResumeEditor ref="resumeEditor" :markdown="currentMarkdown" :enableHtml="enableHtml"></ResumeEditor>
  </div>

</template>
<style>
  
</style>

<script>
import StyleEditor from './components/StyleEditor'
import ResumeEditor from './components/ResumeEditor'
export default {
  name: 'App',
  data(){
    return {
      interval:0,
      currentStyle:'',
      enableHtml:false,
      fullStyle:[`/*
 * hi，我是李念。
 */

/* 添加一个过渡，使变化看起来更柔和 */
* {
  transition: all 0.3s;
}
/* 加个背景色 */
body {
  background: #3e205e;
}
/* 给代码加个边框 */
#options {
  width: 100%;
  border: 1px solid #CFD8DC;
  background: #CFD8DC;
  padding: 16px;
  overflow: auto;
  margin:16px;
}

/* 让代码高亮起来 */
.token.comment, .token.punctuation {
  color: #757575;
}
.token.selector {
  color: #007400;
}
.token.property {
  color: #cf1f1f;
}

/* 现在开始写简历啦！ */

/* 让代码框腾出一些的位置给我的简历框 */
#options {
  width: 32%;
}
/* 准备一个白板 */
#paper {
  flex: 1;
  background: #fdfdfd;
  margin: 16px;
  overflow: auto;
  white-space: pre-wrap;
  font-size: 14px;
}

/* 接下来，请看右边 */

`,

`
/* 这个简历好像差点什么
 * 对了，这是 Markdown 格式的，我需要变成对 HR 更友好的格式
 * 简单，用开源工具翻译成 HTML 就行了
 */
`
,    
 `
/* 调整我的简历，让它变得再好看一点 */
#paper {
  white-space: unset;
  padding: 0 32px;
}
#paper a {
  color: #60206b;
}
#paper ul {
  padding-left: 20px;
}
code{
    padding: 2px 4px;
    margin-right: 4px;
    border-radius: 4px;
    color: #c9b8cc;
    background-color: #60206b;
    height: 18px;
    line-height: 18px;
    font-size: 90%;
    font-family: Consolas,monospace,serif;
  }
/* 让每个模块上下间隔明显一点 */
#paper > div {
  margin: 28px 0;
}

/* 接下来是精细的调整 */

/* 首先，调整我的“基础信息”板块 */
#paper h1 {
  font-size: 22px;
  margin-bottom: 10px;
}

/* 然后是详细介绍模块 */
#paper h2 {
  font-size: 16px;
  border-bottom: 1px solid #60206b;
  padding-bottom: 6px;
  margin-bottom: 6px;
}
#paper h3 {
  display: inline-block;
  font-size: 14px;
  margin: 6px 0;
}
ul>li{
  margin-bottom:4px;
}

`  ],
      currentMarkdown:'',
      fullMarkdown:`# 李念
- 13163387909 | 3038055649@qq.com | 武汉
- Github: https://github.com/linian
 前端开发工程师

## 专业技能
- Vue
    - 有 Vue 的开发经历，熟悉Vue常用的功能及命令，如组件、Vue-Router、Vuex、生命周期、双向绑定等
- jQuery
    -  熟悉 jQuery 常用 API ，如 DOM 操作、特效、事件等。曾使用原生 JavaScript 封装简易版的 $.ajax()
- 移动端开发
    - 会使用 REM 、 vw / vh 、 媒体查询等技术制作适配手机设备的页面
- HTML5, CSS3 & JavaScript
    - 能够根据HTML5标准书写出符合语义化的html代码。如标签header、main、section、footer 等。能够使用flex、float+清除浮动布局，能够用多种方式进行水平居中、垂直居中。
    - 掌握原生JavaScript（ES6），掌握new、DOM操作、闭包、原型链、继承等相关概念的原理和使用方法
    - 掌握 CSS3 动画、过渡、弹性盒子布局、媒体查询等响应式设计常用技术
- 其他
    - 微信小程序
    - 理解虚拟DOM
    - 理解 MVC 、 MVVM 思想，掌握 HTTP 基础等
    - 能够使用Canvas的部分API进行画图，并用Canvas做了《Canvas画板》，并在画板中添加了笔头粗细选择、橡皮檫、撤回、清空、下载和颜色选择等功能。
    - 了解命令行，能够使用命令行进行常用的操作。了解git，能够使用git的命令行进行代码版本的管理，并写了相应博客。
    
## 项目经验

### Vue重构有赞商城
- 关键词：\`Vue\`、\`Vue-cli\`、\`Vue-Router\`、\`Vuex\`、\`Velocityjs\`、\`mint-ui\`、\`qs\`
- 源码链接：https://github.com/linian1226/youzan
- 预览链接：https://gigi1226.top/dist/index.html
- 描述：该项目利用Vue框架重构了有赞商城，对商城的首页、目录分类页、商品搜索列表页、商品详情页、购物车页面以及个人中心地址管理页面进行了重构，在重构过程中个，Vue作为项目的基础框架，利用mint-ui实现了商品列表的下拉请求和加载，利用Velocity实现了一些简单的页面动画效果，利用swiper实现了轮播，利用qs库实现了对url查询参数的解析，利用Vue-Router实现了对地址管理页面的组件路由的管理和切换，利用Vuex实现了对地址管理页面的数据状态的管理和组件间数据的通讯。

### 简历生成器
- 关键词：\`Vue\`、\`async\`、\`Promise\`、\`Markdown\`
- 源码链接：
- 预览链接：
- 描述：该项目实现了一个 Markdown 简历的制作过程，应用vue框架和使用 Promise 处理异步操作，利用 async函数+await。该项目通过动态向\`style\`标签和\`pre\`标签添加文本，使用prism.js实现代码高亮，用marked.js将markdown文件转为HTML

### 简易画板
- 关键词：\`JavaScript\`、\`Canvas\`、\`ES6\`、\`特性检测\`
- 源码链接：https://github.com/linian1226/canvas
- 预览链接：https://linian1226.github.io/canvas/
- 描述：该项目使用原生JavaScript和Canvas标签实现了一个口袋画板的应用，主要调用 Canvas API，实现了线粗、调色、橡皮擦、撤回、清空和保存的功能。用 context.clearRect()实现了橡皮檫和清空的功能，用className切换实现了颜色切换的功能，通过控制lineWidth的大小来调节线粗，用meta:vp、特性检测、ontouch事件以及禁止触发默认事件实现了触屏设备与web端兼容。

### 微信翻译小程序
- 关键词：\`百度翻译api\`、\`md5加密\`、\`ES6\`
- 源码链接：https://github.com/linian1226/weixin-translate
- 描述：支持中、英、法、韩、日、泰、阿拉伯、西班牙语、葡萄牙语、匈牙利语的翻译。该工具还能保存用户翻译记录以便之后查看。

### 手机端网易云音乐
- 关键词：\`jQuery\`、\`CSS3 过渡动画\`、\`组件化思想\`、\`媒体查询\`\`vw/vh\`、\`适配移动端\`、
- 源码链接：https://github.com/linian1226/music-demo
- 预览链接：https://linian1226.github.io/music-demo/
- 描述：该项目使用了jQuery制作了一个仿照网易云音乐的音乐播放器以及对应的后台管理页面，音乐播放器支持歌曲的暂停、 切换和播放的功能，并在歌曲播放时自带滚动字幕以及播放动画效果；后台管理页面支持歌曲的上传以及对歌曲内容编辑的功能。这些功能都是基于jQuery和七牛提供的API实现的。

## 教育经历
### 湖北大学 |  大学本科
2014/9 - 2018/6
- 荣誉：两次校二奖学金、一次校三等奖学金（共三学年）
`
    }
  },
  computed:{
    styleCode(){
      return '<style>'+ this.code + '</style>'
    }
  },
  created(){
    this.makeResume()
  },
  components: {
    StyleEditor,
    ResumeEditor
  },
  methods:{
    makeResume: async function(){//语法糖
      await this.progressivelyShowStyle(0)
      await this.progressivelyShowResume()
      await this.progressivelyShowStyle(1)
      await this.showHtml()
      await this.progressivelyShowStyle(2)
      await this.showPdf()
    },
    showHtml(){
      return new Promise((resolve,reject)=>{
        this.enableHtml = true
        resolve()
      })
    },
    showPdf(){
      setTimeout(() => {
        let options = document.querySelectorAll('#options')[0]
        options.style.display = 'none'
      }, 1000)
    },
    progressivelyShowStyle(n){
      return new Promise((resolve,reject) =>{
        let interval = this.interval
        let showStyle = (async function (){
          let style = this.fullStyle[n]
          if(!style) return
          //计算前n个style的字符总数
          let length = this.fullStyle.filter((_, index) => index <= n).map(item => item.length).reduce((p,c)=>p+c)
          let prefixLength = length - style.length //前n-1个style的字符个数
          if(this.currentStyle.length < length){
            let l = this.currentStyle.length - prefixLength //当前style已经打上的长度
            let char = style.substring(l,l+1) || ' ' //从当前style已经打上的长度打起
            this.currentStyle += char
            if (style.substring(l - 1, l) === '\n' && this.$refs.styleEditor) {
              this.$nextTick(() => {
                this.$refs.styleEditor.goBottom()
              })
            }
            setTimeout(showStyle, interval)
          }else {
            this.$nextTick(() => {
                this.$refs.resumeEditor.goTop()
            })
            resolve()
          }
        }).bind(this)
        showStyle()
      })
    },
    progressivelyShowResume(){
      return new Promise((resolve,reject) =>{
        let length = this.fullMarkdown.length
        let interval = this.interval
        let showResume = () =>{
          if(this.currentMarkdown.length <length){
            this.currentMarkdown = this.fullMarkdown.substring(0,this.currentMarkdown.length+1)
            let prevChar = this.currentMarkdown[this.currentMarkdown.length - 2]
            if(prevChar === '\n' && this.$refs.resumeEditor){
              this.$nextTick(()=>this.$refs.resumeEditor.goBottom())//修改数据之后，dom更新后执行
            }
            setTimeout(showResume, interval)
          }else{
            resolve()
          }
        }
        showResume()
      })
    }
  }
}
</script>
<style scoped>
@import './style.css';
</style>

