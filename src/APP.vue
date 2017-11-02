<template>
  <div id='app'>
    <VueUEditor @ready="editorReady" :defaultMsg="defaultMsg" style="width: 800px" ref="ue"></VueUEditor>
    <button @click="handleSubmit">获取内容</button>
  </div>
</template>

<script>
import VueUEditor from './components/UEditor';
export default {
  name: 'app',
  components: { VueUEditor },
  data () {
    return {
      defaultMsg: 'Demo Text...'
    };
  },
  methods: {
    editorReady (editorInstance) {
      editorInstance.setContent('Hello world!<br>你可以在这里初始化编辑器的初始内容。');
      editorInstance.addListener('contentChange', () => {
        console.log('编辑器内容发生了变化：', editorInstance.getContent());
      });
    },
    // 表单提交前获取 UEditor 内容
    handleSubmit () {
      console.log(this.$refs.ue.getUEContent());
    }
  },
  mounted () {
    // mock response as server
    setTimeout(() => {
      this.defaultMsg = 'You have received a message.';
    }, 2000);
  }
};
</script>
