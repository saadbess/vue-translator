<template>
  <div id="app">
    <h1>Translator</h1>
    <p>A simple translator app powered by Vue</p>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from "./components/TranslateForm";
import TranslateOutput from "./components/TranslateOutput";

export default {
  name: "App",
  components: {
    TranslateForm,
    TranslateOutput
  },
  data: function() {
    return {
      translatedText: ""
    };
  },
  methods: {
    translateText: function(text, language) {
      this.$http
        .get(
          "https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20181002T100920Z.3115274c80ba42c5.7c9f1741727c4050b8e1a68ae3b2e9e30fe0b880&lang=" +
            language +
            "&text=" +
            text
        )
        .then(response => {
          this.translatedText = response.body.text[0];
        });
    }
  }
};
</script>

<style>
#app {
}
</style>
