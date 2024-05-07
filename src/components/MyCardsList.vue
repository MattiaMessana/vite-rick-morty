<script>
  import { store } from "../store";
  import MyCard from "./MyCard.vue";

  export default {
    components: {
        MyCard,
    },
    props: {
        cardsArray: Array,
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
        <div class="row row-cols-4 mt-5 text-center">
            <div class="col-12 col-sm-6 col-md-3" v-for="card in cardsArray">
                <MyCard :cardObj="card" />
            </div>
        </div>
    </div>


</template>

<style scoped lang="scss">


</style>
