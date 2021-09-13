<template>
  <div class="task-input my-list">
    <input v-model="title" placeholder="Title" type="text">
    <input v-model="cost" placeholder="Cost" type="text">
    <input v-model="quantity" placeholder="Quantity" type="text">
    <button @click="onAddTask">Add task</button>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  emits: {
    onAddTask({ title, cost, quantity }) {
      if(title === '' || cost === '' || quantity === '' ) {
        alert('Fill some info please!')
        return false
      }
      return true
    }
  },
  setup(props, { emit }) {
    const title = ref('')
    const cost = ref('')
    const quantity = ref('')

    const onAddTask = () => {
      emit('onAddTask', { title: title.value, cost: cost.value, quantity: quantity.value })
    }

    return {
      title,
      cost,
      quantity,
      onAddTask
    }
  }
}
</script>

<style scoped>
.task-input {
  margin: 10px 0;
}
</style>