<template>
  <div>
    <div>{{ name }}</div>
    <input type="text" :value="name" />
    <button type="button" @click="hello">click</button>
  </div>
</template>

<script setup>
import {ref} from 'vue';
// 데이터 바인딩 v-bind: -> : / v-on:click -> @click 으로 사용 가능
const name = ref("hrkim");

const hello = () => {
  name.value = "coding";
}
</script>