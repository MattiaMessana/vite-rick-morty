<script>

import { store } from "../store";

export default {
    data() {
        return {
            store,
            statusList: [ "All" , "Alive" , "Dead" , "Unknow"],
        }
    }
}

</script>

<template>
    <div class="container py-4">
        <div class="d-flex justify-content-between">
            <div>
                <select @change="$emit('filter')" v-model="store.activeStatus">
                <option :value="status" v-for="status in statusList">
                    {{ status }}
                </option>
                </select>
            </div>

            <p>Mostrati {{ store.cardsList.length }} elementi</p>
        </div>
  </div>

</template>

<style lang="scss" scoped>


</style>