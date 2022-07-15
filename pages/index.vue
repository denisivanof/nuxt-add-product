<template>
    <add-product @add="add" />
    <product :products="products" @del="del"/>
</template>
<script setup>
import {ref, onMounted} from 'vue'
import AddProduct from "../components/AddProduct";
import Product from "../components/Product";

onMounted(() => {
  if(localStorage.getItem('products')){
    products.value = JSON.parse(localStorage.getItem('products'))
  }
})
const products = ref([])
const add = (e) => {
  products.value.push({...e, id: Date.now()})
  localStorage.setItem('products', JSON.stringify(products.value))
}
const del = (e) => {
 products.value = products.value.filter(item=>item.id !== e)
}
</script>
<style lang="scss">
</style>

