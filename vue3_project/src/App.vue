<template>
  <div class="container">
    <h2>To-Do List</h2>
    <!-- modifiers - e.preventDefault 대신 사용-->
    <form @submit.prevent="onSubmit" class="d-flex">
      <div class="flex-grow-1 mr-2">
        <input 
          class="form-control" 
          type="text" 
          v-model="todo" 
          placeholder="Type new to-do"
        />
      </div>
      <div>
        <button type="submit" class="btn btn-primary" @click="onSubmit">Add</button>
      </div>
    </form>
      {{ todos }}
  </div>
</template>

<script setup>
  import { ref, reactive } from 'vue';

  const todo = ref('');
  const todos = reactive([]);

  const onSubmit = () => {
    /* 기본적인 refresh하는 속성을 예방
    e.preventDefault();
    */

    todos.push({
      id: Date.now(),
      subject: todo.value
    });
  }
</script>