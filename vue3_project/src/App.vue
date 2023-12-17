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

    <div v-if="!todos.length">추가된 Todo가 없습니다.</div>

    <div class="card mt-2" 
      v-for="(todo, index) in todos" 
      :key="index">
      <div class="card-body p-2 d-flex align-items-center">
        <div class="form-check flex-grow-1">
          <input type="checkbox" class="form-check-input" v-model="todo.completed" />

          <label class="form-check-label" :class="{ todo: todo.completed }">{{ todo.subject }}</label>
        </div>
        <div>
          <button type="button" class="btn btn-danger btn-sm" @click="deleteTodo(index)">Delete</button>
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

  const deleteTodo = (index) => {
    todos.splice(index, 1);
  }
</script>

<style scoped>
  .todo {
    color: gray;
    text-decoration: line-through;
  }
</style>