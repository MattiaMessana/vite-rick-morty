<script>
  import { store } from "./store";
  import axios from "axios";
  import MyTitle from "./components/MyTitle.vue";
  import MyCardsList from "./components/MyCardsList.vue";
  import MySearchBar from "./components/MySearchBar.vue";

  export default {
    components: {
      MyTitle,
      MyCardsList,
      MySearchBar,

    },
    data() {
      return {
        store,
      };
    },
    created() {
      this.getCards();
    }, 
    methods: {
      getCards() {

        const paramsObj = {
          status: "",
        }

        if (this.store.activeStatus !== "All") {
          paramsObj.status = this.store.activeStatus;
        }

        axios
        .get("https://rickandmortyapi.com/api/character/", {
          params: paramsObj,
        })
        .then((resp) => {
        this.store.cardsList = resp.data.results;
        })
        
      }
  }

  };

</script>

<template>

  <MyTitle />
  <MySearchBar @filter="getCards"/>
  <MyCardsList :cardsArray="store.cardsList"/>

</template>

<style lang="scss">


</style>
