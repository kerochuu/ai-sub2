<template>
  <div>
    <button id="google_translate_element" v-on:click="googleTranslateElementInit">Translate!</button>
  </div>
</template>

<script>
export default {
  name: 'Translate',
  methods: {
    googleTranslateElementInit() {
      new google.translate.TranslateElement({
        to: 'en'
      }, "google_translate_element");
    }
  }
};
</script>


