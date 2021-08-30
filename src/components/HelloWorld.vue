<template>
  <h1>{{ msg }}</h1>
</template>
  
<script setup lang="ts">
/**
 * 1、不需要手动传入依赖
 * 2、不是lazy初始化都会执行分析依赖
 * 3、无法获取初始值
 * 4、一些异步操作 放里面更加合适
 * 5、watch第三个参数处理副作用的第一个参数
 */
import { ref, defineProps, watchEffect, onMounted } from 'vue'
defineProps({
  msg: String
})

const num = ref(0);
onMounted(() => {
  console.log('onMounted');
})

const stop = watchEffect((onInvalidate) => {
  /* 副作用 */
  console.log('watchEffect之前调用', num.value);
  onInvalidate(() => {
    console.log('副作用即将执行时或者监听器停止监听，调用~', num.value);
  })
}, {
  onTrigger(e) { // 将在依赖项变更导致副作用被触发时被调用
    // debugger
    console.log('将在依赖项变更导致副作用被触发时被调用', num.value);

  }
})

setTimeout(() => {
  console.log('开始改变依赖', num.value);
  num.value++
  console.log('改变依赖了', num.value);
}, 1000)

</script>
  
<style scope>
</style>