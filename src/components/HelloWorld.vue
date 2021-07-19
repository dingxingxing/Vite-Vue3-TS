<template>
  <h1>{{msg}}</h1>
  测试
  {{ count }}
</template>

<script setup lang="ts">
import { ref, reactive, defineProps } from 'vue'
// ref就是一般某个元素，简单数据类型   reactive对象
defineProps({
  msg: String
})

const count = ref(0)
console.log('count', count.value);
count.value++
console.log('count2',count.value);


</script>