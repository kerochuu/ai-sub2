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
#google_translate_element {
  border: 2px solid red;
  font-weight: bold;
  font-size: 1.2rem;
  color:#f0f0f0;
}
</style>
