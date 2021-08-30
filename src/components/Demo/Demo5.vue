<template>
  <h1>{{ msg }}</h1>
  <h2>{{ state.count }}</h2>
  <h2>{{ count }}</h2>
  <h2>{{ state2.count.count }}</h2>
</template>
  
<script setup lang="ts">

import { ref, reactive, watch, defineProps, onMounted } from 'vue'
defineProps({
  msg: String
})
const state = reactive({ count: 0 });
const count = ref(0)
const state2 = reactive({ count: { count: 100 } })

watch(() => state.count, (count, prevCount) => {
  console.log('侦听一个getter', count, prevCount);
}, {
  immediate: true, // 立即执行
})

watch(count, (count, prevCount) => {
  console.log('直接侦听一个ref', count, prevCount);

})

watch(() => state2.count.count, (count, prevCount) => {
  console.log('深度监听obj', count, prevCount);
}, {
  immediate: true,
  deep: true
})

const value1 = ref(10)
const value2 = ref(20)

watch([value1, value2], ([value1, value2], [prevValue1, prevValue2]) => {
  console.log('侦听多个数据源one', value1, prevValue1);
  console.log('侦听多个数据源two', value2, prevValue2);
})

setTimeout(() => {
  // state.count++
  // count.value--
  // state2.count.count++
  value1.value++
  value2.value++
}, 1000)

</script>
  
<style scope>
</style>