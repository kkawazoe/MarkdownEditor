<template>
  <div class="editor row full-height">
    <div class="page-title">
      <p>Markdown Editor</p>
    </div>
    <div class="col-xs-6 full-height">
      <textarea v-model="source" class="source full-height syncscroll" name="scroll-area">
      </textarea>
    </div>
    <section class="result-area col-xs-6 full-height">
      <vue-markdown
        class="markdown-preview result-html full-height syncscroll"
        name="scroll-area"
        :source="source"
        :watches="['source']"
        :show="show"
        @rendered="highlight()">
      </vue-markdown>
    </section>
  </div>
</template>

<style src="../../static/vendor/css/prism.min.css"></style>

<style lang="scss" scoped>

.editor {
  .page-title {
    margin-top: 15px;
    position: relative;
    min-height: 1px;
    padding-right: 15px;
    padding-left: 15px;
    > p {
      font-size: 24px;
      font-weight: 600;
    }
  }
  .source{
    width: 100%;
    font-size: 13px;
    padding: 2px
  }

  .result-html {
    padding: 2px 10px;
    overflow: auto;
    border: 1px solid rgb(153, 153, 153);
    border-radius:4px;
    background-color: inherit;
  }
}

</style>

<script>
import VueMarkdown from 'vue-markdown'
import Prism from '../../static/vendor/js/prism.min.js'

export default {
  name: 'editor',
  data: () => {
    return {
      source: '',
      show: true,
      html: false,
      breaks: true,
      linkify: false,
      emoji: true,
      typographer: true,
      toc: false
    }
  },
  components: {
    VueMarkdown
  },
  methods: {
    highlight () {
      Prism.highlightAll()
    }
  }
}
</script>
