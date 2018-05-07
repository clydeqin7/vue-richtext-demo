<template>
  <div class="components-container">
    <div class="info">UE编辑器示例<br>需要使用编辑器时，调用UE公共组件即可。可设置填充内容defaultMsg，配置信息config(宽度和高度等)，可调用组件中获取内容的方法。</div>
    <div class="editor-container">
      <UE :defaultMsg=defaultMsg :config=config ref="ue"></UE>
    </div>
    <div>
      <button @click="showUEmessage">保存为word到本地</button>
    </div>
  </div>
</template>

<script>
  import UE from '@/components/UE';
  export default {
    components: {UE},
    data() {
      return {
        defaultMsg: '这里是UE测试',
        config: {
//          toolbars: [
//            ['fullscreen', 'source', 'undo', 'redo'],
//            ['bold', 'italic', 'underline', 'fontborder', 'strikethrough', 'superscript', 'subscript', 'removeformat', 'formatmatch', 'autotypeset', 'blockquote', 'pasteplain', '|', 'forecolor', 'backcolor', 'insertorderedlist', 'insertunorderedlist', 'selectall', 'cleardoc']
//          ],
          initialFrameWidth: null,
          initialFrameHeight: 350
        }
      }
    },
    methods: {
      showUEmessage () {
        let content = this.$refs.ue.getUEContentTxt()
        console.log(content)
        let uriContent = "data:application/octet-stream," + encodeURIComponent(content);
        console.dir(uriContent)
        window.open(uriContent, 'neuesDokument');
      },
    }
  };
</script>

<style>
  .info{
    border-radius: 10px;
    line-height: 20px;
    padding: 10px;
    margin: 10px;
    background-color: #ffffff;
  }
</style>
