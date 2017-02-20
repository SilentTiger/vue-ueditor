<template>
  <div id="app">
    <VueUEditor @ready="editorReady" style="width: 800px"></VueUEditor>
  </div>
</template>

<script>
  import VueUEditor from './components/UEditor';
  export default {
    name: 'app',
    components: { VueUEditor },
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
