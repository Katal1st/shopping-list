<template>
  <div class="task-card my-style">
    <div>
      <h4>Title:{{ model.title }}</h4>
      <p>Cost:{{ model.cost }}$</p>
      <p>Quantity:{{ model.quantity }}</p>
      <p>Sum:{{ model.cost * model.quantity }}$</p>
      

    </div>
    <div class="task-card__buttons">
      <div class="task-card__checkbox">
      <input type="checkbox" id="checkbox" v-model="checked">
      <label for="checkbox">{{ checked }}</label>
      </div>
      <button @click="emitOnRemove" >x</button>
    </div>
  </div>
</template>

<script>  
export default {
  emits: ['onDone', 'onRemove', 'onChecked'],
  computed: {

  },
  props: {
    model: {
      required: true,
      default: {
        id: 0,
        title: 'Create video',
        cost: 'And upload on YouTube',
        quantity:21,
        status: false
      }
    }
  },
  setup(props, { emit }) {
    const emitOnChecked = () => {
      emit('onChecked')
    }

    const emitOnRemove = () => {
      emit('onRemove')
    }

    return {
      emitOnRemove
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