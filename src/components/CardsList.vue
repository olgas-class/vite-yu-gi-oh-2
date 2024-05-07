<script>
import { store } from "../store";
import AppCard from "./AppCard.vue";

export default {
  components: {
    AppCard,
  },
  data() {
    return {
      store,
    };
  },
};
</script>

<template>
  <div class="container">
    <div class="row row-cols-4">
      <div class="col" v-for="card in store.cardsList">
        <AppCard :cardObj="card" />
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped></style>
