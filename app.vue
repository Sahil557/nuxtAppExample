<template>
  <div>
    
     <!-- Render the list of items -->
    <div>
      <h1 v-for="(item, index) in items" :key="index">{{ item }}</h1>
    </div>

    <!-- Conditionally rendered Add List button -->
    <button v-if="!showInput" @click="showInput = true">Add List</button>
    
    <!-- Conditionally rendered input field and Add Item button -->
    <div v-if="showInput">
      <input v-model="item" placeholder="Enter item">
      <button @click="addItem">Add Item</button>
    </div>
    
   
  </div>
</template>

<script setup>
import { ref } from 'vue';

// Reactive state to control visibility
const showInput = ref(false);
const item = ref('');
const items = ref([]);

// Method to handle adding an item
const addItem = () => {
  if (item.value.trim()) {
    items.value.push(item.value); // Add the item to the list
    item.value = ''; // Clear the input field
  }
};
</script>
