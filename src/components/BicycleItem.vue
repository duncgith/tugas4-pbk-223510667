<template>
  <div 
    @click="selectBicycle" 
    @mouseover="hoverBicycle" 
    @mouseleave="leaveBicycle"
  >
    <h3>{{ bicycle.name }}</h3>
    <p>Price: ${{ bicycle.price }}</p>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue'

const props = defineProps({
  bicycle: Object
})

const emit = defineEmits(['select', 'hover', 'leave'])

const selectBicycle = () => {
  emit('select', props.bicycle)
}

const hoverBicycle = () => {
  emit('hover', props.bicycle)
}

const leaveBicycle = () => {
  emit('leave')
}
</script>

<style scoped>
div {
  border: 1px solid #ccc;
  padding: 10px;
  margin: 10px;
  cursor: pointer;
}
</style>
