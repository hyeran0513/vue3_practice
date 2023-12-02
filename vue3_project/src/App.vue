<template>
  <div>
    <button 
      type="button" 
      class="btn btn-primary" 
      v-on:click="updateStringSample">
      {{ stringSample }}
    </button>

    <button 
      type="button" 
      class="btn btn-secondary" 
      v-on:click="updateArraySample">
      {{ arraySample }}
    </button>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue';

// 문자열, 배열, 객체 등 모두 사용 가능하나 사용 시 value를 붙여야 함
const stringSample = ref('hrkim');

// 배열이나 객체일 경우 reactive 사용
const arraySample = reactive({ id: 'hrkim' });

const updateStringSample = () => {
  stringSample.value = 'hrkim2';
} 

const updateArraySample = () => {
  arraySample.id = 'hrkim3';
}
</script>

<style scoped>

</style>