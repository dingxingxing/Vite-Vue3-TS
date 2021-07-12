<template>
  
</template>

<script lang="ts">
import { defineComponent } from "vue";
import css from '../../assets/index.css'
export default defineComponent ({
  name: "HelloWorld",
  setup() {
    // 代码这里
  }
})
</script>

<template>
  <h1>{{ msg }}</h1>

  <p>
    <a href="https://vitejs.dev/guide/features.html" target="_blank">
      Vite Documentation
    </a>
    |
    <a href="https://v3.vuejs.org/" target="_blank">Vue 3 Documentation</a>
  </p>

  <button type="button" @click="state.count++">count is: {{ state.count }}</button>
  <h3 class="text">components/HelloWorld.vue</h3>
  <h1>{{ num }}</h1>
</template>

<!-- <script setup lang="ts">
import { defineProps, ref, reactive, onMounted  } from 'vue'
const color = "red"
const font = {
  size: "3rem"
}
defineProps({
  msg: String
})
ref: num = 100;

const state = reactive({ count: 0 })

onMounted: {
  $num = 200;
  console.log("挂载", $num);
}
</script>

<style scoped>
/* :root {
  --varColor: yellowgreen;
} */
a {
  color: var(--varColor);
}
.text {
  color: v-bind(color);
  font-size: v-bind("font.szie");
}
</style> -->
