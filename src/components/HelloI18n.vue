<template>
  <p>{{ t("cat", { name: "Мурка" }) }}</p>
  <p>{{ t("dog") }}</p>
  <p>{{ t("horse") }}</p>
  <p>{{ t("crocodile") }}</p>
  <p>{{ t("email", { email }) }}</p>

  <p>{{ t("person", 0) }}</p>
  <p>{{ t("person", 1) }}</p>
  <p>{{ t("person", 2) }}</p>

  <p>{{ d(new Date(), "long", locale) }}</p>
  <p>{{ n(1000, "currency", locale) }}</p>

  <button @click="setLocale('en')">English</button>
  <button @click="setLocale('ru')">Русский</button>
</template>

<script>
  import { defineComponent } from "vue";
  import { useI18n } from "vue-i18n";

  export default defineComponent({
    name: "HelloI18n",
    setup() {
      const { t, tc, d, n, locale } = useI18n({
        inheritLocale: true,
        useScope: "global",
      });

      const setLocale = (code) => {
        locale.value = code;
        localStorage.setItem("locale", code);
      };

      const email = "me@example.ru";

      locale.value = localStorage.getItem("locale");
      if (!locale.value) {
        setLocale(navigator.language);
      }

      return { t, tc, d, n, locale, setLocale, email };
    },
  });
</script>
