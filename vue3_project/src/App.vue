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

    <!-- 반복문: v-for -->
    <div class="card mt-2" v-for="(todo, i) in todos" :key="i">
      <div class="card-body p-2">
        {{ todo.subject }}
      </div>
    </div>
    </div>
  </div>
</template>

<script setup>
  import { ref, reactive } from 'vue';

  const hasError = ref(false);

  const todo = ref('');
  const todos = reactive([
    { id: 1, subject: '휴대폰 사기' },
    { id: 2, subject: '장보기' }
  ]);

  const onSubmit = () => {
    if (todo.value) { 
      hasError.value = false;

      todos.push({
        id: Date.now(),
        subject: todo.value
      });
    } else {
      hasError.value = true;
    }
  }
</script>