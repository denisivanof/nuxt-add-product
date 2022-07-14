<template>
  <article class="card-product">
    <button class="card-product__btn" @click="emit('del', item.id)"></button>
    <img class="card-product__img" :src="item.linkImg">
    <div class="card-product__item">
      <h3 class="card-product__name">{{ item.name }}</h3>
      <p class="card-product__description">{{item.description}}</p>
      <div class="card-product__price">{{item.price}}</div>
    </div>
  </article>
</template>

<script setup>
const props = defineProps(['item'])
const emit = defineEmits(['del'])

</script>

<style scoped lang="scss">
@import "assets/scss/card-product.scss";
</style>
