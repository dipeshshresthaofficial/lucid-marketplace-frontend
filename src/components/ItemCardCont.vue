<template>

    <div id="items-cont">
        <div v-for="(item,index) in filteredProducts" v-bind:key="index">
            <ItemCard :item="item"/>
        </div>
        
    </div>
</template>

<script>
import ItemCard from './ItemCard.vue';
// import data from './../../data.json';

export default{
    name: 'ItemCardCont',
    components: {
        ItemCard,
    },
    props: ['filteredProducts'],
    data(){
        return{
        }
    }
}
</script>
<style>
#items-cont{
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-evenly;
    background-color: #f1efef;
    
  height: 88vh;
  overflow-y: auto;
}
</style>