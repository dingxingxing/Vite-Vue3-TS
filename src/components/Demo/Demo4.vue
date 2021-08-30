<template>
  <h1>{{ msg }}</h1>
  <h2>plusOne：{{ plusOne }}</h2>
  <h2>count：{{ count }}</h2>
  <div ref="root">22121</div>
  <br />
  <!-- <div style="background-color:#e5edff;">
    <img style="width:191px;" src="@/assets/mm1.jpg" alt="">
    <span>xxx</span>
  </div>-->
</template>

<script lang="ts" setup>
import { computed, ref, defineProps, onMounted, defineComponent } from 'vue'

defineProps({
  msg: String
});

const count = ref(1);
const root = ref(null);
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
onMounted(() => {
  console.log("🐻", root.value);
})

plusOne.value = 100
</script>
  
<style scope>
</style>