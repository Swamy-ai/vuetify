<template>
<div class="d-flex flex-column justify-center align-center">
<v-card width="50%" class="d-flex flex-column justify-center purple lighten-4 mb-2">
    
  <div class="py-3 my-2 px-3" v-bind:class="{'is-complete':todo.completed}">
    <p class="pt-3"> 
      <input type="checkbox" class="mr-2" v-on:change="markComplete" v-bind:checked="todo.completed">
      {{todo.title}}
      <v-btn @click="$emit('del-todo', todo.id)" class="pink darken-1 float-right white--text" fab x-small>x</v-btn>
      </p>
  </div>
  
</v-card>
</div>
</template>

<script>
export default {
  name: "TodoOne",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
}
</script>

<style scoped>
  .is-complete {
    text-decoration: line-through;
  }
</style>