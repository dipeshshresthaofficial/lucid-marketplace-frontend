<template>
    <div id="filterbar-cont">
        
        <input type="text" v-model="searchText" @change="$emit('onUserInput',searchText)" placeholder="Type to search.."/>
        <div  id="checkbox-cont">
            <p>Categories</p>
            <div v-for="item in categories" v-bind:key="item">
                <input type="checkbox" v-model="selectedCategory" :value="item" name="category"/>
                <label :for="item" v-text="item"></label>
            </div>
        </div>
        <button @click="$emit('onSelectedCategory',selectedCategory)">Search</button>
        
    </div>
</template>


<script>
export default{
    name: 'FilterBar',
    props: ['categories'],
    data(){
        return{
            searchText: "",
            selectedCategory: [],
        }
    },
    methods:{
        // emitSearchText(){
        //     this.$emit('name',"dipesh");
        // }
    }
    
}
</script>


<style>
#filterbar-cont{
    display: flex;
    flex-direction: column;
    /* justify-content: center; */
    align-items: center;
    padding: 60px 10px 0 10px;

}
#filterbar-cont input,#filterbar-cont button{
    text-decoration: none;
    outline: none;
    border-radius: 5px;
    padding: 5px 10px;
    border: 1px solid grey;
}

#filterbar-cont button{
    width: 100%;
}
#checkbox-cont{
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 100%;
    margin: 20px 0;
    /* padding: 10px;/= */
}
#checkbox-cont div{
    text-align: left;
    /* padding: 0 50px; */
}

#checkbox-cont div input{
    margin-right: 5px;
}

</style>