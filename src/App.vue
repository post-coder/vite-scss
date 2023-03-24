<script>
import AppTitle from "./components/AppTitle.vue";
import AppHero from "./components/AppHero.vue";

// iniziare la notazione Vue
export default {
  data() {
    return {
      viewTitle: true,
    };
  },

  components: {
    AppTitle,
    AppHero,
  },
};
</script>

<template>
  <AppTitle v-if="viewTitle"></AppTitle>

  <AppHero></AppHero>
</template>

<style scoped></style>
