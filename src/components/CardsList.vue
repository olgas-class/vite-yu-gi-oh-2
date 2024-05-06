<script>
import AppCard from "./AppCard.vue";

export default {
  components: {
    AppCard,
  },
  props: {
    cardsArray: Array,
  },
  data() {
    return {};
  },
};
</script>

<template>
  <div class="container">
    <div class="row row-cols-4">
      <div class="col" v-for="card in cardsArray">
        <AppCard :cardObj="card"/>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped></style>
