<template>
  <div class="todo_block">
    <p class="todo_block__title">{{todo.name}}</p>
    <form @submit.prevent="addItem" v-bind:blockId="todo.id" class="todo_item__add--block">
      <input v-model="itemText" type="text">
      <button class="todo_item_add">Добавить</button>
    </form>
    <ul v-if="todo.items.length!=0" class="todo_item">
      <li v-for="todoItem in todo.items" :key="todoItem.id" class="todo_item_list">{{todoItem.name}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "ItemAdd",
  props: ['todo'],
  data: function () {
    return {
      itemText: ''
    }
  },
  methods: {
    addItem(){
      console.log(this.itemText)
    }
  }
}
</script>

<style scoped>

</style>