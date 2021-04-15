<template>

  <p>{{ t("cat") }}</p>
  <p>{{ t("dog") }}</p>
  <p>{{ t("horse") }}</p>
  <p>{{ t("crocodile") }}</p>
  
    <button @click="locale='en'">English</button>
    <button @click="locale='ru'">Русский</button>

</template>

<script>
import { defineComponent } from "vue";
import { useI18n } from "vue-i18n";

export default defineComponent({
  name: "HelloI18n",
  setup() {
    const { t, locale } = useI18n({
      locale:'en',
      inheritLocale: true,
      useScope: "global",
    });

    return { t, locale };
  },
});
</script>
