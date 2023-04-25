<template>
    <div id="items-cont">
        <div v-for="(item,index) in data" v-bind:key="index">
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
    props: [],
    data(){
        return{
            data: []
        }
    },
    methods:{
        async fetchMarketplaceData(){
            
            console.log("----------Fetching... ----------");
            const res = await fetch('http://localhost:5959/api');
            // console.log(res.json());
            const data = await res.json();
            console.log("----------fetch data----------");
            console.log(data.data);
            return data.data;
        }
    },
    async created(){
        this.data = await this.fetchMarketplaceData();
    }
}
</script>
<style>
#items-cont{
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-evenly;
}
</style>