<template>
       <div class="Rectangle_2" v-for="n in this.cards" :key="n">
         <Card :geometry="this.geometry" />
       </div>
</template>
<script>
import Card from "./Card.vue"

export default {
    name: "Cards",
    props: {
        cards: Number,
        geometry: Number
    },
    components: {
        Card
    }
}

</script>


<style scoped>

.Rectangle_2{
    display: flex;
    padding: 12px 0px 0px 12px;
    background: #000000;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 4px;
    margin-top: 36px;
    margin-bottom: 35px;
    
}
</style>