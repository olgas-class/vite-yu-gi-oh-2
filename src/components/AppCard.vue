<script>
export default {
  props: {
    cardObj: Object,
  },
  computed: {
    image() {
      return this.cardObj.card_images[0].image_url_small;
    },
    archetype() {
      return this.cardObj.archetype
        ? this.cardObj.archetype
        : "nessun archetipo";
    },
  },
};
</script>

<template>
  <div class="card">
    <img :src="image" alt="" />
    <div class="card-body">
      <h4>{{ cardObj.name }}</h4>
      <p>{{ archetype }}</p>
    </div>
  </div>
</template>

<style lang="scss" scoped></style>
