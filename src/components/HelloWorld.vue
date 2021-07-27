<template>
  <h1>{{ msg }}</h1>
  <h2>plusOne：{{ plusOne }}</h2>
  <h2>count：{{ count }}</h2>
</template>

<script setup lang="ts">
import { computed, ref, defineProps, onMounted} from 'vue'

defineProps({
  msg: String
});
const count = ref(1);
// const plusOne = computed(() => count.value + 1)
// console.log('plusOne:', plusOne);
// 返回一个readonly 触发警告
// plusOne.value++
const plusOne = computed({
  get: () => count.value,
  set: (val) => {
    count.value = val
  }
})

plusOne.value = 100
</script>
  
<style scope>
  
</style>