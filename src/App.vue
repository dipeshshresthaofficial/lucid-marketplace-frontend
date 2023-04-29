<template>
  <div id="container">

    <HeaderComp class="header" />
    <ItemCardCont class="itemcard" :filteredProducts="filteredProducts" />
    <FilterBar class="filterbar" :categories="categories" @on-user-input="getUserInput" @on-selected-category="getSelectedCategory"/>
  </div>
</template>

<script>
import HeaderComp from './components/HeaderComp.vue';
import ItemCardCont from './components/ItemCardCont.vue';
import FilterBar from './components/FilterBar.vue';

export default {
  name: 'App',
  components: {
    HeaderComp,
    ItemCardCont,
    FilterBar
  },
  data(){
    return{
      categories: ['home','furniture','auto','electronics','fashion'],
      data: [],
      filteredProducts: [],
      searchText: "",
      selectedCategory: [],

    }
  },
  methods:{
      async fetchMarketplaceData(){
          
          console.log("----------Fetching... ----------");
          const res = await fetch('https://lucid-marketplace.onrender.com/api ');
          // console.log(res.json());
          const data = await res.json();
          console.log("----------fetch data----------");
          // console.log(data);
          return data;
      },
      searchProduct(){
            this.filteredProducts = this.data.filter(item=>{
                if(this.selectedCategory.length!=0){

                    return item.name.toLowerCase().includes(this.searchText.toLowerCase())&& this.selectedCategory.includes(item.category.toLowerCase())
                }else{
                    return item.name.toLowerCase().includes(this.searchText.toLowerCase());
                }
        });
            console.log(this.filteredProducts);
            // console.log(this.data);
        },
        getUserInput(value){
          console.log(value);
          this.searchText = value;
          this.searchProduct();
        },
        getSelectedCategory(value){
          this.selectedCategory = value;
          this.searchProduct();
        }
  },
  async created(){
      this.data = await this.fetchMarketplaceData();
      // Initially when website loads there won't be any user input so filtered products will contain all the products.
      this.filteredProducts = this.data;
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat&display=swap');
*{
  font-family: 'Montserrat', sans-serif;
  margin: 0;
  padding: 0;
  overflow-y: hidden;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px;
  margin: 0 40px; */
  /* display: flex;
  justify-content: center; */
  overflow: hidden;
}

.header{
  grid-area: header;
  width: 100%;
  box-shadow: 4px 5px 30px -9px rgba(0, 0, 0, 0.64);
  z-index: 999;
}
.itemcard{
  grid-area: itemcard;
  /* border: 1px solid red; */
}
.filterbar{
  grid-area: filterbar;
  box-shadow: 4px 5px 30px -9px rgba(0, 0, 0, 0.64);
  max-width: 190px;
}

#container{
  display: grid;
  grid-template-areas: 
  'header header'
  'filterbar itemcard';
  grid-template-columns: 0.18fr 1fr;
  position: relative;
}

</style>
