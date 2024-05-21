<template>
  <div>
    <BicycleItem 
      v-for="(bicycle, index) in bicycles" 
      :key="index" 
      :bicycle="bicycle" 
      @select="selectBicycle"
      @hover="hoverBicycle"
      @leave="leaveBicycle"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import BicycleItem from './BicycleItem.vue'

const bicycles = ref([
  { name: 'Mountain Bike', price: 500, description: 'Great for off-road adventures with durable suspension.' },
  { name: 'Road Bike', price: 700, description: 'Perfect for high-speed riding on paved roads with lightweight design.' },
  { name: 'BMX', price: 300, description: 'Ideal for tricks and stunts with strong and compact frame.' }
])

const emit = defineEmits(['selectBicycle', 'hoverBicycle', 'leaveBicycle'])

const selectBicycle = (bicycle) => {
  emit('selectBicycle', bicycle)
}

const hoverBicycle = (bicycle) => {
  emit('hoverBicycle', bicycle)
}

const leaveBicycle = () => {
  emit('leaveBicycle')
}
</script>
