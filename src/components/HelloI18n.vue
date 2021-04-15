<template>

  <p>{{ t("cat") }}</p>
  <p>{{ t("dog") }}</p>
  <p>{{ t("horse") }}</p>
  <p>{{ t("crocodile") }}</p>
  
    <button @click="setLocale('en')">English</button>
    <button @click="setLocale('ru')">Русский</button>

</template>

<script>
import { defineComponent } from "vue";
import { useI18n } from "vue-i18n";

export default defineComponent({
  name: "HelloI18n",
  setup() {
    
    const { t, locale } = useI18n({
      inheritLocale: true,
      useScope: "global",
    });

    const setLocale = (code) =>{
      locale.value = code
      localStorage.setItem("locale",code)
    }

    locale.value = localStorage.getItem("locale")
    if (!locale.value){
      setLocale(navigator.language)
    }

    return { t, locale, setLocale };
  },
});
</script>
