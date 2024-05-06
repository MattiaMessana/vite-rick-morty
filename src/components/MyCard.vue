<script>
    export default {
        props: {
            cardObj: Object,
        },
    }
</script>

<template>
    <div class="card mt-4 p-3 border-0">

        <img :src="cardObj.image" class="card-img-top rounded-circle" alt="...">

        <div class="card-body">
            <h5 class="card-title mb-4"> {{this.cardObj.name}}</h5>
            <p class="card-subtitle"> {{this.cardObj.status}} </p>
            <p class="card-subtitle"> {{this.cardObj.species}} </p>
        </div>
    </div>
    
</template>

<style lang="scss" scoped>


</style>