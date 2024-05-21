<script setup>
import BicycleShop from './components/BicycleShop.vue'
</script>

<template>
  <div>
    <BicycleShop>
      <template #details="{ bicycle }">
        <p>Description: This {{ bicycle.name }} is a great choice for both beginners and experienced riders!</p>
      </template>
    </BicycleShop>
  </div>
</template>

<style scoped>
div {
  text-align: center;
  margin-top: 50px;
  font-family: STHupo;
}
</style>
