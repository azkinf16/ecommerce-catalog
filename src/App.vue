<script setup>
import ProductDisplay from "./components/ProductDisplay.vue";
</script>

<template>
  <main>
    <div class="center">
      <div class="box">
        <ProductDisplay />
      </div>
    </div>
  </main>
</template>

<style>
.center {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.box {
  background: white;
  width: 100%;
  max-width: 950px;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
}
</style>