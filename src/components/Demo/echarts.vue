<template>
  <div>echarts</div>

  <div id="customerChart" class="custom"></div>
</template>
  
<script lang="ts" setup>
import { ref, defineProps, onMounted, inject, defineComponent } from 'vue'

let echarts: any = inject("ec");//引入
onMounted(() => {
  try {
    let myChart = echarts.init(document.getElementById("customerChart"));
  // 绘制图表
  myChart.setOption({
    title: { text: "掌握程度" },
    tooltip: {},
    xAxis: {
      type: 'category',
      boundaryGap: false,
      data: ["","一二三四五六七八九十一", "利用直线方向向量与平面法向量解决计算问", "2-5", "12-3", "4-7", "6-8", "7-9", "12-8", "12-9"],
      axisLabel: {  
        interval:0,  
        rotate:40 ,
        // 换行
        formatter: function(value:any){
            var str = value.slice(0,10) + '\n' + value.slice(10)
            return str
        },
      },
    },
    // legend: {
      // data: ["用户量","搜索引擎","数据"]
    // },
    yAxis: {},
    grid: {
      left: '3%',
      right: '4%',
      bottom: '3%',
      containLabel: true
    },
    series: [
      {
        name: "用户量",
        type: "line",
        symbol: "circle",
        symbolSize: 16,
        data: ["",3, 4, 2, 3, 4, 5, 4, 3],
        smooth:false,   //关键点，为true是不支持虚线的，实线就用true
        itemStyle:{
            normal:{
                lineStyle:{
                    width:2,
                    type:'dotted'  //'dotted'虚线 'solid'实线
                }
            }
        },   
      },
      {
        name: '搜索引擎',
        type: 'line',
        data: ["",4, 3, 2, 2, 3, 4],
        symbol: 'circle', 
        symbolSize: 16,
        itemStyle: {
          color:(value:any) => {
            console.log('value:',value);
            if(value.data > 3) {
              return 'red'
            } else if(value.data >2) {
              return 'green'
            } else {
              return 'blue'
            }
          }
        }
      },
    //   {
    //     type: 'graph',
    //     layout: 'none',
    //     coordinateSystem: 'cartesian2d',
    //     symbolSize: 16,
    //     label: {
    //       show: false,
    //       normal: {
    //       show : false,//显示
    //         position: 'right',//相对于节点标签的位置，默认在节点中间
    //         //回调函数，你期望节点标签上显示什么
    //         formatter: function(params:any){
    //             return '';
    //         },
    //       }
    //     },
    //     edgeSymbol: ['', 'arrow'],
    //     edgeSymbolSize: [4, 10],
    //     data: ["",5, 2, 4, 2, 3, 5],
    //     links: [
    //       {
    //         source: '0',
    //         target: '1'
    //       },
    //       {
    //         source: '1',
    //         target: '2'
    //       },
    //       {
    //         source: '2',
    //         target: '3'
    //       },
    //       {
    //         source: '3',
    //         target: '4'
    //       },
    //       {
    //         source: '4',
    //         target: '5'
    //       },
    //       {
    //         source: '5',
    //         target: '6'
    //       },
    //     ],
    //     lineStyle: {
    //       color: '#2f4554'
    //     }
    //   }
    ],
  });
  } catch (e) {
    console.log(e);
    
  }
  
})
</script>
  
<style scope>
.custom {
  /* width: 1100px; */
  /* height: 600px; */
}
</style>