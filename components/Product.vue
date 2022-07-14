<template>
  <div class="product">
    <div class="product__sort">
      <div class="product__sort-select"
           @click="open"
      >{{select}}
        <div style="margin-left: 5px">
          <svg xmlns="http://www.w3.org/2000/svg" width="8" height="6" viewBox="0 0 8 6" fill="none">
            <path d="M7.48532 1.24264L4.24268 4.48528L1.00003 1.24264" stroke="#B4B4B4"/>
          </svg>
        </div>
      </div>
      <ul v-if="isOpen" class="product__sort-dropdown" @click="dropdownSelect">
        <li>По наименованию</li>
        <li>По цене min</li>
        <li>По цене max</li>
      </ul>
    </div>
    <div class="product__items">
      <card-product v-for="item  in products" :key="item.id" :item="item" @del="emit('del', item.id)"/>
    </div>
  </div>
</template>

<script setup>
import {ref} from "vue";
import CardProduct from "./CardProduct";
const props = defineProps(['products'])
const emit = defineEmits(['del'])

const select = ref('По умолчанию')
const isOpen = ref(false)
const open = () => {
  isOpen.value ? isOpen.value = false : isOpen.value = true
}
const dropdownSelect = (e) => {
  select.value = e.target.innerText
  open()
}
</script>

<style scoped lang="scss">
@import "assets/scss/product.scss";
</style>
