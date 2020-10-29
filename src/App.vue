<template>
<div id="app">
  <ProductCarousel msg="Welcome to Your Vue.js App"/>
  <SubImages />
  <h1 class="product-name">{{name}}</h1>
  <RatingVue />
  <h1 class="product-price">$ {{price}}</h1>
  <VariantSelector />
  <QuantitySelectorVue v-on:updateQty="updateQty" />
  <AddToCartVue v-on:order="order" />
  <p class="offer-text">Buy now and save $ 10</p>
  <DetailsVue />
  </div>
</template>

<script>
import AddToCartVue from './components/AddToCart.vue'
import ProductCarousel from './components/Carousel'
import DetailsVue from './components/Details.vue'
import QuantitySelectorVue from './components/QuantitySelector.vue'
import RatingVue from './components/Rating.vue'
import SubImages from './components/SubImages'
import VariantSelector from './components/VariantSelector.vue'
import axios from 'axios'
export default {
  name: 'App',
  components: {
    ProductCarousel,
    SubImages,
    AddToCartVue,
    QuantitySelectorVue,
    VariantSelector,
    DetailsVue,
    RatingVue
  },
  data: ()=>{
    return{
      qty:1,
      price: 13.99,
      name: 'Sunshine Bliss Daily Vitamin D',
    }
  },
  methods:{
    updateQty(i){
      this.qty= i;
    },
    order(){
      axios.post('http://localhost:4192/api/v1/order', {order_qty : this.qty, value:this.price, product_name:this.name})
    }
  }
}
</script>

<style lang='scss'>
*{
    font-family: DM Sans;
    font-style: normal;
    font-weight: bold;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.product-name, .product-price, .offer-text{
font-family: DM Sans;
font-style: normal;
font-weight: bold;
text-align: center;

}
.product-name{
font-size: 28px;
line-height: 36px;
margin-left: 24px;
margin-right: 24px;
}
.product-price{
font-size: 36px;
}
.offer-text{
  margin-top: 15px;
  margin-bottom: 15px;
  color: #32C574;
}
</style>
