<script>
  import { store } from "./store";
  import axios from "axios";
  import MyTitle from "./components/MyTitle.vue";
  import MyCardsList from "./components/MyCardsList.vue";
  import MySearchBar from "./components/MySearchBar.vue";
  import MyLoader from "./components/MyLoader.vue";

  export default {
    components: {
      MyTitle,
      MyCardsList,
      MySearchBar,
      MyLoader,

    },
    data() {
      return {
        store,
        loading: false,
      };
    },
    created() {
      this.getCards();
    }, 
    methods: {
      getCards() {
        this.loading = true;
        
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
        this.loading = false;
        })
        
      }
  }

  };

</script>

<template>

  <MyTitle />
  <MySearchBar @filter="getCards"/>
  <MyLoader v-if="loading"/>
  <MyCardsList v-else :cardsArray="store.cardsList"/>

</template>

<style lang="scss">


</style>
