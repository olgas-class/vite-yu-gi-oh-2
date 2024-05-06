<script>
import axios from "axios";
import AppHeader from "./components/AppHeader.vue";
import CardsList from "./components/CardsList.vue";

export default {
  components: {
    AppHeader,
    CardsList,
  },
  data() {
    return {
      cardsArray: [],
    };
  },
  created() {
    axios
      .get("https://db.ygoprodeck.com/api/v7/cardinfo.php", {
        params: {
          num: 20,
          offset: 0,
        },
      })
      .then((resp) => {
        console.log(resp);
        this.cardsArray = resp.data.data;
      });
  },
};
</script>

<template>
  <AppHeader />
  <CardsList :cardsArray="cardsArray" />
</template>

<style lang="scss"></style>
