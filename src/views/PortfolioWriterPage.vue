<template>
  <div>
    <ImgBanner imgSrc="https://source.unsplash.com/5brvJbR1Pn8/1600x900">
      <div style="line-height:1.2em;font-size:1.2em;" slot="text">Write your Portfolio</div>
    </ImgBanner>

    <v-container>
      <v-layout>
        <v-flex sm-12 md-6>
          <markdown-editor v-model="content" ref="markdownEditor"></markdown-editor>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>
 
<script>
import ImgBanner from "../components/ImgBanner";
import markdownEditor from "vue-simplemde/src/markdown-editor";

export default {
  components: {
    ImgBanner,
    markdownEditor
  }
};
</script>
 
 
<style scoped>
  @import '~simplemde/dist/simplemde.min.css';
  
</style>
