<template>
<section class="add">
  <h2 class="add__h2">Добавление товара</h2>
  <form class="add__form">
    <div class="add__form-item">
      <label class="add__form-label add__form-label--req">Наименование товара</label>
      <input class="add__form-input"
             placeholder="Введите наименование товара"
             v-model="name"
             @focus="onFocus"
             @blur="onBlur"

      />
    </div>
    <div class="add__form-item">
      <label class="add__form-label">Описание товара</label>
      <textarea class="add__form-input add__form-input--text"
                placeholder="Введите описание товара"
                v-model="description"
      />
    </div>
    <div class="add__form-item">
      <label class="add__form-label add__form-label--req">Ссылка на изображение товара</label>
      <input class="add__form-input"
             placeholder="Введите ссылку"
             v-model="linkImg"
      />
    </div>
    <div class="add__form-item">
      <label class="add__form-label add__form-label--req">Цена товара</label>
      <input class="add__form-input"
             placeholder="Введите цену"
             v-model="price"
      />
    </div>
    <button class="add__form-btn" @click.prevent="submit">
      Добавить товар
    </button>
  </form>
</section>
</template>

<script setup>
import {ref} from 'vue'

const name = ref('')
const description = ref('')
const linkImg = ref('')
const price = ref('')


const onFocus = (e)=>{
  console.log(e)
}
const onBlur = (e)=>{
  console.log(name.value)
}
const submit = () => {
  console.log(name.value)
  console.log(description.value)
  console.log(linkImg.value)
  console.log(price.value)
}
</script>
<style lang="scss">
@import "assets/scss/add-product.scss";
</style>
