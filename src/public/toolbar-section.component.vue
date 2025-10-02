<template>
  <header>

    <div class="logo">

      <img src="/GigLog.png" alt="gigMap Logo" />


    </div>

    <nav>
      <router-link
          v-for="item in items"
          :key="item.label"
          :to="item.to"
          class="nav-button"
      >
        {{ $t(item.label) }}
      </router-link>
    </nav>

    <language-switcher />


    <a href="" class="btn-appweb">
      {{ $t("ingresar") }}
    </a>
  </header>

  <router-view />
</template>

<script>
import LanguageSwitcher from "./language-switcher.component.vue";

export default {
  name: "toolbar-section",
  components: { LanguageSwitcher },
  data() {
    return {
      items: [
        { label: "inicio", to: "/home" },
        { label: "fans", to: "/fans" },
        { label: "artistas", to: "/artists" }
      ]
    };
  }
};
</script>

<style scoped>

</style>
