<template>
  <div>
    <div class="container">
    <h2>To-Do List</h2>
    <form @submit.prevent="onSubmit">
      <div class="d-flex">
        <div class="flex-grow-1 mr-2">
          <input 
            class="form-control" 
            type="text" 
            v-model="todo" 
            placeholder="Type new to-do"
          />
        </div>
        <div>
          <button type="submit" class="btn btn-primary">Add</button>
        </div>
      </div>

      <div v-show="hasError" style="color: red">
        This field cannot be empty
      </div>
    </form>

    <div class="card mt-2" v-for="(todo, i) in todos" :key="i">
      <div class="card-body p-2">
        <div class="form-check">
          <input type="checkbox" class="form-check-input" v-model="todo.completed" />
          <!-- style 바인딩 
          <label class="form-check-label" :style="todo.completed ? todoStyle : {}">{{ todo.subject }}</label>
          -->
          <!-- class 바인딩 -->
          <label class="form-check-label" :class="{ todo: todo.completed }">{{ todo.subject }}</label>
        </div>
      </div>
    </div>
    </div>
  </div>
</template>

<script setup>
  import { ref, reactive } from 'vue';

  const hasError = ref(false);

  const todo = ref('');
  const todos = reactive([]);
  /*
  const todoStyle = {
    textDecoration: 'line-through',
    color: 'gray'
  };
  */
  const onSubmit = () => {
    if (todo.value) {
      todos.push({
        id: Date.now(),
        subject: todo.value,
        completed: false
      });
      
      hasError.value = false;
      todo.value = '';
    } else {
      hasError.value = true;
    }
  }
</script>

<style scoped>
  .todo {
    color: gray;
    text-decoration: line-through;
  }
</style>