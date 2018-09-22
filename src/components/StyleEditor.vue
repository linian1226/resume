<template>
  <div id="options" ref="container">
    <div class="code" v-html="codeInStyleTag"></div>
    <pre id="code_body"  v-html="highlightedCode"></pre>
    <a class="downloadResume" href="resume.pdf" target="_blank" download="前端开发" v-show="isShow">下载 PDF 简历</a>
  </div>
</template>

<script>
import Prism from 'prismjs'
export default {
    name:'Editor',
    props:['code','isShow'],//向子组件传数据
    computed:{
        highlightedCode(){
            return Prism.highlight(this.code,Prism.languages.css)
        },
        codeInStyleTag(){
            return `<style>${this.code}</style>`
        }
    },
    methods:{
        goBottom(){
            this.$refs.container.scrollTop = 100000
        }
    }
}
</script>
