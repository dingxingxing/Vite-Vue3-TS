<template>
  <div>echarts</div>

  <div id="customerChart" class="custom"></div>
</template>
  
<script lang="ts" setup>
import { ref, defineProps, onMounted, inject, defineComponent } from 'vue'

let echarts: any = inject("ec");//引入
onMounted(() => {
  let myChart = echarts.init(document.getElementById("customerChart"));
  // 绘制图表
  myChart.setOption({
    title: { text: "" },
    tooltip: {},
    xAxis: {
      data: ["帶我去多惡趣味呵呵輔導輔導", "12-帶我去多惡趣味呵呵輔導輔導", "帶我去多惡趣味呵呵輔導輔導-5", "12-帶我去多惡趣味呵呵輔導輔導", "帶我去多惡趣味呵呵輔導輔導-7", "帶我去多惡趣味呵呵輔導輔導-8", "帶我去多惡趣味呵呵輔導輔導-9", "12-帶我去多惡趣味呵呵輔導輔導", "12-帶我去多惡趣味呵呵輔導輔導"],
    },
    yAxis: {},
    series: [
      {
        name: "用户量",
        type: "line",
        data: [3, 4, 2, 3, 4, 5, 4, 3],
      },
      {
        name: '搜索引擎',
        type: 'line',
        stack: '总量',
        data: [4, 3, 3, 2, 3, 4]
      }
    ],
  });
})
</script>
  
<style scope>
.custom {
  width: 1100px;
  height: 600px;
}
</style>