<template>
  <h1>{{msg}}</h1>
  测试
  {{ count }}
  <h3>toRefs解构reactive：{{ name }}</h3>
  
</template>

<script setup lang="ts">
import { ref, reactive, defineProps, toRefs } from 'vue'
// ref就是一般某个元素，简单数据类型   reactive对象
defineProps({
  msg: String
})

const count = ref(0)

console.log('count', count.value);
count.value++
console.log('count2',count.value);

// 使用reactive包裹单独的ref
const state = reactive({
  count
});
console.log('state', state);
const obj = reactive({
  name: 'yuyu',
  address: '合肥'
})

const { name } = {...toRefs(obj)}

</script>