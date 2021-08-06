<template>

<div id="nav" >
  <router-link :class="{active: $route.name ==='Home'}" to="/">Home</router-link>
  <router-link :class="{active: $route.name ==='Cart'}" to="/cart">Cart</router-link>
</div>
  <router-view/>
</template>

<script>

export default{
  mounted(){
    this.$store.commit('updateCartFromLocalStorage')
  }
}
</script>

<style lang="scss">
#app{
  text-align: center;
}
html,body{
   margin: 0;
  padding: 0;
  overflow-x: hidden;

}

body{
  background-color: #fff;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#nav{
  padding: 20px;
  width: 100%;
  height: 30px;
  line-height: 10px;
  background-color:rgb(49, 143, 49);
  a{
    font-weight: bold;
    color: rgb(235, 227, 227);
    text-decoration: none;
    margin:0 5px 0 5px;
    font-size:1.80rem;


    &.active{
      color: #2c3e50;
    }
  }
}

.text-center{
  text-align: center;
}

</style>
