<script>
import { store } from "./store";
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import CardsList from "./components/CardsList.vue";
import AppLoader from "./components/AppLoader.vue";
import AppSearchBar from "./components/AppSearchBar.vue";

export default {
  components: {
    AppHeader,
    CardsList,
    AppLoader,
    AppSearchBar,
  },
  data() {
    return {
      store,
      isLoading: false,
    };
  },
  created() {
    this.getCards();
  },
  methods: {
    getCards() {
      this.isLoading = true;

      // Costuriamo i parametri per la chiamata axios
      const paramsObj = {
        num: 20,
        offset: 0,
      };

      // Se c'è il filtro applicato, aggiungo anche chiave archetype all'oggetto di params
      if (this.store.selectedArchetype !== "All") {
        paramsObj.archetype = this.store.selectedArchetype;
      }

      console.log("Get cards", this.store.selectedArchetype);
      axios
        .get("https://db.ygoprodeck.com/api/v7/cardinfo.php", {
          params: paramsObj,
        })
        .then((resp) => {
          this.store.cardsList = resp.data.data;
          this.isLoading = false;
        });
    },
  },
};
</script>

<template>
  <AppHeader />
  <AppSearchBar @filter="getCards" />
  <AppLoader v-if="isLoading" />
  <CardsList v-else />
</template>

<style lang="scss"></style>
