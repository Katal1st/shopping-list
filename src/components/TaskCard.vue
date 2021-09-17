<template>
  <div class="task-card my-style">
    <div>
      <h4>Title:{{ model.title }}</h4>
      <p>Cost:{{ model.cost }}$</p>
      <p>Quantity:{{ model.quantity }}</p>
      <p>Sum:{{ sum }}$</p>
    </div>
    <div class="task-card__buttons">
      <div class="task-card__checkbox">
      <input type="checkbox" id="checkbox" @click="emitOnDone" v-model="checked" >
      </div>
      <button @click="emitOnRemove" >x</button>
    </div>
  </div>
</template>

<script>  
export default {
  emits: ['onDone', 'onRemove', ],
  props: {
    model: {}
  },
  setup(props, { emit }) {
    const emitOnDone = () => {
      emit('onDone')
    }

    const emitOnRemove = () => {
      confirm('remove position?') ? emit('onRemove') : ''; 
    }

    return {
      emitOnDone,
      emitOnRemove
    }
  },
    computed: {
    sum() {
      return this.model.cost * this.model.quantity
    }
  }
}


</script>

<style scoped>
.task-card {
  display: flex;
  justify-content: space-between;
  align-items: center;


}
  .task-card__buttons {
  display: flex;
  justify-content: space-between;
}

.task-card__checkbox {
  margin-right:50px;
}


</style>