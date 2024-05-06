<script>
  import axios from "axios";
  import MyTitle from "./components/MyTitle.vue";
  import MyCardsList from "./components/MyCardsList.vue";

  export default {
    components: {
      MyTitle,
      MyCardsList,

    },
    data() {
      return {
        cardsArray: [],
      };
    },
    created() {
    axios
      .get("https://rickandmortyapi.com/api/character")
      .then((resp) => {
        console.log(resp);
        this.cardsArray = resp.data.results;
        console.log(this.cardsArray);
      });
  },

  };

</script>

<template>
  <MyTitle />
  <MyCardsList :cardsArray="cardsArray"/>
</template>

<style lang="scss">


</style>
