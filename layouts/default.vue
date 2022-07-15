<template>
    <header>
    </header>
    <main class="main">
      <slot />
    </main>
    <footer>
    </footer>
</template>
<script setup>
</script>
<style lang="scss">
.main{
  height: 100vh;
  padding: 32px 32px 0 32px;
  @media (max-width: 1092px) {
    padding: 32px 10px 0 10px;
  }
}
</style>

