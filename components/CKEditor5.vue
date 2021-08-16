<template>
  <div>
    <div
      class="ckeditor"
      v-bind:class="[
        { ckeditorCharactersSurpassed: maxNumberOfCharactersSurpassed },
      ]"
    >
      <ckeditor
        :editor="editor"
        v-model="dataEditor"
        :config="editorConfig"
      ></ckeditor>
      <label class="numberOfWords"
        >{{ numberOfWords }}/{{ maxNumberOfCharacters }}</label
      >
    </div>
    <label class="errorMessage" v-if="maxNumberOfCharactersSurpassed"
      >Superaste el maximo de caracteres permitidos</label
    >
  </div>
</template>

<script>
let ClassicEditor;
let CKEditor;
if (process.client) {
  ClassicEditor = require("ckeditor5-custom-build/build/ckeditor");
  CKEditor = require("@ckeditor/ckeditor5-vue2");
} else {
  CKEditor = { component: { template: "<div></div>" } };
}
export default {
  props: {
    onChangeDataEditor: Function,
    maxNumberOfCharacters: Number,
  },
  data() {
    return {
      maxNumberOfCharactersSurpassed: false,
      numberOfWords: 0,
      editor: ClassicEditor,
      dataEditor: "",
      editorConfig: {
        toolbar: {
          items: [
            "bold",
            "italic",
            "underline",
            "strikethrough",
            "|",
            "bulletedList",
            "numberedList",
            "alignment",
            "|",
            "undo",
            "redo",
          ],
        },
        wordCount: {
          onUpdate: (stats) => {
            let actualNumberOfCharacters = stats.characters;
            this.numberOfWords = actualNumberOfCharacters;
            this.maxNumberOfCharactersSurpassed =
              actualNumberOfCharacters > this.maxNumberOfCharacters;
          },
        },
      },
    };
  },
  watch: {
    dataEditor: function() {
      this.onChangeDataEditor(this.dataEditor);
    },
  },
  components: {
    ckeditor: CKEditor.component,
  },
};
</script>

<style>
.ckeditor {
  position: relative;
  text-align: right;
}
.ckeditorCharactersSurpassed {
  border: 1px solid red;
}
.numberOfWords {
  position: absolute;
  bottom: 5px;
  right: 10px;
  font-size: 14px;
}
.errorMessage {
  color: #ff4040;
  font-size: 13px;
}
</style>
