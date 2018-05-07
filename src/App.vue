<template>
  <div class="components-container">
    <!-- bidirectional data binding（双向数据绑定） -->
    <quill-editor v-model="content"
                  ref="myQuillEditor"
                  :options="editorOption"
                  @blur="onEditorBlur($event)"
                  @focus="onEditorFocus($event)"
                  @ready="onEditorReady($event)">
    </quill-editor>

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
    computed: {
      editor() {
        return this.$refs.myQuillEditor.quill
      }
    },
    mounted() {
      console.log('this is current quill instance object', this.editor)
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
