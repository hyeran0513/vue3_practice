<template>
  <div>
    <!--
    아래 코드 대신 v-model를 사용하면 더 간단하게 구현 가능
    <input type="text" :value="name" @input="updateName" />
    -->
     <input type="text" v-model="name" />
    <button class="btn btn-primary" v-on:click="onSubmit">click</button>
  </div>
</template>

<script setup>
import {ref} from 'vue';

const name = ref('hrkim');

const onSubmit = () => {
  console.log(name.value);
};

/* 양방향 바인딩 
1. @input: input에 값이 들어갈 때 실행 
2. click 버튼 누르면 name의 값을 e.target.value으로 변경

const updateName = (e) => {
  name.value = e.target.value;
};
*/
</script>