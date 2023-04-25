<template>
    <div class="card-outer-cont">
        <div class="item-img-cont">
            <img :src="item.imageUrl" :alt="item.name"/>
        </div>
        <div class="item-detail">
            <span class="date-seller">{{ item.dateFirstAdded }} by {{ item.seller }} </span>
           
            <p><b>${{ item.price }}</b></p>
            <p v-text="item.name"></p>
            <span class="location" v-text="item.location"></span>
        </div>
    </div>
</template>

<script>
export default{
    name: 'ItemCard',
    props: ['item'],
    data(){
        return{

        }
    }
}
</script>

<style scoped>
.card-outer-cont{
    /* border: 1px solid green; */
    margin: 15px;
    box-shadow: 4px 5px 30px -9px rgba(228, 228, 228, 0.64);
}
.item-img-cont{
    min-width: 300px;
    min-height: 130px;
    width: 200px;
    height: 300px;
    border-radius: 15px;
    /* border: 1px solid black; */
    margin: 0 auto;
    overflow: hidden;
}

.item-img-cont img{
    max-width: 100%;
    max-height: 100%;
    width: 100%;
    height: 100%;
    object-fit: cover;
}
.item-detail{
    text-align: left;
    padding: 5px 0px;
}
.item-detail span{
    color: grey;
    
    font-size: 13px;
    /* opacity: 0.8; */
    display: block;
}

.date-seller{
    margin-bottom: 10px;
}

.location{
    margin: 10px 0;
}
</style>