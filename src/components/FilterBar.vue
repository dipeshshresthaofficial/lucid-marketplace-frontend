<template>
    <div id="filterbar-cont">
        
        <input type="text" v-model="searchText" @change="$emit('onUserInput',searchText)" placeholder="Type to search.."/>
        <div  id="checkbox-cont">
            <div id="categories-header">
                <p>Categories</p>
                <span @click="clearCheckbox">clear</span>
            </div>
            <div v-for="item in categories" v-bind:key="item">
                <input type="checkbox" v-model="selectedCategory" :id="item" :value="item" name="category"/>
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
        clearCheckbox(){
            const checkboxes = document.querySelectorAll('[name="category"]');
            checkboxes.forEach(checkbox=>{
                checkbox.checked = false;
                this.selectedCategory=[];
                this.$emit('onSelectedCategory',this.selectedCategory);
        })
        }
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
    background-color: #d8d8d8;
    color: #014746;
}
#filterbar-cont input,#filterbar-cont button{
    text-decoration: none;
    outline: none;
    border-radius: 5px;
    padding: 8px 10px;
    border: 1px solid grey;
    color: #014746;
}

#filterbar-cont button{
    width: 100%;
    background-color: #014746;
    color: #fff;
    cursor: pointer;
}
#checkbox-cont{
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 100%;
    margin: 20px 0;
    /* padding: 10px;/= */
}
#checkbox-cont div, #checkbox-cont p{
    text-align: left;
    /* padding: 0 50px; */
}

#categories-header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 10px;

}
#categories-header span{
    text-decoration: underline;
    cursor: pointer;
    font-size: 0.8em;
}
#categories-header p{
    font-weight: 700;
}
#checkbox-cont div input{
    margin-right: 5px;
    accent-color: #014746;
}

</style>