<template>
  <div id="app">
    <VueUEditor v-model="content" @ready="editorReady" style="width: 800px"></VueUEditor>
    <h1>预览</h1>
    <div class="content" v-html="content"></div>
  </div>
</template>

<script>
  import VueUEditor from './components/UEditor';
  export default {
    name: 'app',
    components: { VueUEditor },
    data () {
      return {
        content: ''
      };
    },
    methods: {
      editorReady (editorInstance) {
        editorInstance.setContent('Hello world!<br>你可以在这里初始化编辑器的初始内容。');
        editorInstance.addListener('contentChange', () => {
          console.log('编辑器内容发生了变化：', editorInstance.getContent());
        });
      }
    }
  };
</script>
<style>
  .content {
    border: 1px solid #000;
  }
</style>
