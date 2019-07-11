<template>
  <div>
    <button id="google_translate_element" v-on:click="googleTranslateElementInit">Translate!</button>
  </div>
</template>

<script>
export default {
  name: "Translate",
  methods: {
    googleTranslateElementInit() {
      new google.translate.TranslateElement(
        {
          pageLanguage: "en, ko",
          includedLanguages: "ko,en",
          layout: google.translate.TranslateElement.InlineLayout.SIMPLE,
          autoDisplay: true
        },

        "google_translate_element"
      );
    }
  }
};
</script>

<style>
.goog-te-banner-frame{
  display:none !important;
}
</style>
