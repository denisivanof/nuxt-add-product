<template>
<section class="add">
  <h2 class="add__h2">Добавление товара</h2>
  <form class="add__form">
    <div class="add__form-item">
      <label class="add__form-label add__form-label--req">Наименование товара</label>
      <input class="add__form-input"
             placeholder="Введите наименование товара"
             v-model="state.name"
             name="name"
             @input="onInput"
             @blur="onBlur"
             :class="{'add__form-input--error': error.name, 'add__form-input--success': success.name}"
      />
      <span v-if="error.name" class="add__form-hint">Поле является обязательным</span>
    </div>
    <div class="add__form-item">
      <label class="add__form-label">Описание товара</label>
      <textarea class="add__form-input add__form-input--text"
                placeholder="Введите описание товара"
                v-model="state.description"
                name="description"
      />
    </div>
    <div class="add__form-item">
      <label class="add__form-label add__form-label--req">Ссылка на изображение товара</label>
      <input class="add__form-input"
             placeholder="Введите ссылку"
             v-model="state.linkImg"
             name="linkImg"
             @input="onInput"
             @blur="onBlur"
             :class="{'add__form-input--error': error.linkImg, 'add__form-input--success': success.linkImg}"
      />
      <span v-if="error.linkImg" class="add__form-hint">Поле является обязательным</span>
    </div>
    <div class="add__form-item">
      <label class="add__form-label add__form-label--req">Цена товара</label>
      <input class="add__form-input"
             placeholder="Введите цену"
             v-model="state.price"
             name="price"
             @input="onInput"
             @blur="onBlur"
             :class="{'add__form-input--error': error.price, 'add__form-input--success': success.price}"
      />
      <span v-if="error.price" class="add__form-hint">Поле является обязательным</span>
    </div>
    <button class="add__form-btn"
            :class="{'add__form-btn--active': isActive}"
            @click.prevent="submit"
    >
      Добавить товар
    </button>
  </form>
</section>
</template>

<script setup>
import {ref, watch, reactive} from 'vue'
const emit = defineEmits(['add'])

const isActive = ref(false)
const state = reactive({
  name: '',
  description: '',
  linkImg: '',
  price: '',
})
const error = reactive({
  name: false,
  linkImg: false,
  price: false,
})
const success = reactive({
  name: false,
  linkImg: false,
  price: false,
})

const setIsActive = ()=>{
  const {name, linkImg,price } = state
  if(name.length && linkImg.length && price.length){
    isActive.value = true
  }else {
    isActive.value = false
  }
}
watch(state, setIsActive)

const onInput = (e)=>{
  if(state[e.target.name].length){
    success[e.target.name] = true
    error[e.target.name] = false
  }
}
const onBlur = (e)=>{
  if(!state[e.target.name].length){
    success[e.target.name] = false
    error[e.target.name] = true
  }
}
const submit = () => {
  if(isActive.value){
    emit('add', state)
  }else {
    for (const key in error) {
      if(!success[key]){
        error[key] = true
      }
    }
  }
}
</script>
<style lang="scss">
@import "assets/scss/add-product.scss";
</style>
