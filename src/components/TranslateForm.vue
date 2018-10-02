<template>
  <div id="translateForm">
    <form v-on:submit="formSubmit">
        <input type="text" v-model="textToTranslate" placeholder="Type here...">
        <select v-model="language">
            <option value="ar">Arabic</option>
            <option value="ru">Russian</option>
            <option value="de">German</option>
            <option value="es">Spanish</option>
            <option value="zh">Chinese</option>
            <option value="cs">Czech</option>
            <option value="ja">Japanese</option>
        </select>
        <input type="submit" value="Translate me">
    </form>
  </div>
</template>

<script>
export default {
  name: "translateForm",
  data() {
    return {
      textToTranslate: "",
      language: ""
    };
  },
  created() {
    this.language = "ar";
  },
  methods: {
    formSubmit(e) {
      this.$emit("formSubmit", this.textToTranslate, this.language);
      e.preventDefault();
    }
  }
};
</script>

<style>
</style>
