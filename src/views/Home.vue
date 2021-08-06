<template>
  <div class="home">
 <Carousel class="carousel"  
      :navigation="true"
      :pagination="true"
      :startAutoPlay="true"
      :timeout="5000" v-slot="{ currentSlide }">
   <Slide v-for="(slide, index) in carouselSlides" :key="index">
<div v-show="currentSlide === index + 1" class="slide-info">
  <img :src="require(`../assets/${slide}.jpg`)" alt="" />
</div>
   </Slide>
 </Carousel>
<h1>Products</h1>
 <ProductDescriptionDrawer 
 :product="product"
 :active="active.product_drawer"
 v-on:close-product-drawer="closeProductDrawer()" />

 <div class="product-cards-container">
   <ProductSummaryCard 
    v-for="product in items" :key="product.id" :product="product" 
    v-on:view-product="viewProduct($event)" />
 </div>

  </div>
</template>

<script>
import Carousel from "../components/Carousel.vue";
import Slide from "../components/Slide.vue";
import items from '../data/items.js';
import ProductSummaryCard from '../components/products/ProductSummaryCard.vue';
import ProductDescriptionDrawer from "../components/products/ProductDescriptionDrawer.vue"

export default {
  name: 'Home',
  components: { 
    Carousel,
    Slide,
    ProductSummaryCard,
    ProductDescriptionDrawer
  },
  data(){
    return{
items:items,
product:null,
active:{
  product_drawer: false
}
    }
  },
  methods:{
viewProduct(product){
  this.product=product
  this.active.product_drawer=true
  console.log(this.product)
},
closeProductDrawer(){
  this.active.product_drawer=false
}
  },
    setup() {
    const carouselSlides = ["bg-1", "bg-2", "bg-3","bg-4"];
    return { carouselSlides };
  },
}
</script>

<style lang="scss" scoped>
.carousel {
  position: relative;
  max-height: 100vh;
  height: 100vh;
  .slide-info {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    max-height: 100%;
    height: 100%;
    img {
      min-width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }
}
.product-cards-container{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>