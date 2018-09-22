<template>
    <div id="paper" :class="{htmlMode:enableHtml}" ref="container">
        <div v-if="enableHtml" v-html="result"></div>
        <pre v-else>{{result}}</pre>
    </div>
</template>
<script>
import marked from 'marked'
export default {
    props:['markdown','enableHtml'],
    name:'ResumeEditor',
    computed:{
        result(){
            return this.enableHtml ? marked(this.markdown) : this.markdown
        }
    },
    methods: {
      goBottom: function () {
        this.$refs.container.scrollTop = 100000
      },
      goTop: function(){
        this.$refs.container.scrollTop = 0
      }
    }
}
</script>


