<template>
  <div>
    <h1>DUnc fixedgear Bicycle Shop</h1>
    <BicycleList 
      @selectBicycle="displaySelectedBicycle" 
      @hoverBicycle="showHoverBicycle" 
      @leaveBicycle="hideHoverBicycle"
    />
    <div v-if="hoverBicycle" class="hover-info">
      <h2>{{ hoverBicycle.name }}</h2>
      <p>{{ hoverBicycle.description }}</p>
    </div>
    <div v-if="showModal" class="modal">
      <div class="modal-content">
        <span class="close" @click="closeModal">&times;</span>
        <h2>{{ selectedBicycle.name }}</h2>
        <p>Price: ${{ selectedBicycle.price }}</p>
        <label>
          Quantity:
          <input type="number" v-model="quantity" min="1">
        </label>
        <p>Total: ${{ totalPrice }}</p>
        <button @click="checkOut">Check Out</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import BicycleList from './BicycleList.vue'

const selectedBicycle = ref(null)
const hoverBicycle = ref(null)
const showModal = ref(false)
const quantity = ref(1)

const displaySelectedBicycle = (bicycle) => {
  selectedBicycle.value = bicycle
  showModal.value = true
}

const closeModal = () => {
  showModal.value = false
}

const checkOut = () => {
  alert(`You have checked out ${quantity.value} ${selectedBicycle.value.name}(s) for a total of $${totalPrice.value}.`)
  // Reset the modal
  closeModal()
  quantity.value = 1
}

const totalPrice = computed(() => {
  return selectedBicycle.value ? selectedBicycle.value.price * quantity.value : 0
})

const showHoverBicycle = (bicycle) => {
  hoverBicycle.value = bicycle
}

const hideHoverBicycle = () => {
  hoverBicycle.value = null
}
</script>

<style scoped>
h1 {
  color: #003099;
}

.hover-info {
  position: fixed;
  bottom: 20px;
  left: 20px;
  background-color: rgba(255, 255, 255, 0.289);
  padding: 10px;
  border: 1px solid #f4f3f3;
}

.modal {
  display: block;
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgb(0,0,0);
  background-color: rgba(0,0,0,0.4);
}

.modal-content {
  background-color: #ffffff55;
  margin: 15% auto;
  padding: 20px;
  border: 1px solid #888;
  width: 80%;
}

.close {
  color: #aaa;
  float: right;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}

button {
  background-color: #048aaf;
  color: rgba(255, 255, 255, 0.241);
  padding: 10px 20px;
  border: none;
  cursor: pointer;
  font-size: 16px;
}

button:hover {
  background-color: #1f22d4;
}
</style>
