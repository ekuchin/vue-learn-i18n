<template>
  <div class="hello">
    <p>{{ text[selectedLanguage].hello }}</p>
    <p>{{ text[selectedLanguage].bye }}</p>
    <button @click="selectedLanguage = 'en'">English</button>
    <button @click="selectedLanguage = 'ru'">Русский</button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      selectedLanguage: "en",
      text: {
        en: {
          hello: "Hello",
          bye: "Bye",
        },
        ru: {
          hello: "Привет",
          bye: "Пока-пока",
        },
      },
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
