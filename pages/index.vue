<template>
    <add-product @add="add" />
    <product :products="products" @del="del"/>
</template>
<script setup>
import {ref} from 'vue'
import AddProduct from "../components/AddProduct";
import Product from "../components/Product";

const products = ref([])
const add = (e) => {
  products.value.push({...e, id: Date.now()})
}
const del = (e) => {
 products.value = products.value.filter(item=>item.id !== e)
}

</script>

<style lang="scss">
 .main{
   //height: 100vh;
   //padding: 32px 32px 0 32px;
 }
</style>

