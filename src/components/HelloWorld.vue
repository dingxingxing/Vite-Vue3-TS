<template>
  
  <div>
    <div class="tage">
      <img class="img" src="https://vitejs.cn/logo.svg" alt="">
      <div>5456454645</div>
    </div>
    
  </div>
  
</template>
  
<script setup lang="ts">
  
import { ref, defineProps, onMounted} from 'vue'

onMounted(() => {
  let moveElem:any = document.querySelector('.img'); //待拖拽元素   \
  console.log('选取到元素：', moveElem);
  
  let dragging:Boolean; //是否激活拖拽状态
  let tLeft:any, tTop:any; //鼠标按下时相对于选中元素的位移

  //监听鼠标按下事件
  document.addEventListener('mousedown', function(e) {
      if (e.target == moveElem) {
          
        dragging = true; //激活拖拽状态
        let moveElemRect = moveElem && moveElem.getBoundingClientRect();
        console.log('走进激活拖动', moveElemRect);
        if(moveElemRect) {
          tLeft = e.clientX - moveElemRect.left; //鼠标按下时和选中元素的坐标偏移:x坐标
          tTop = e.clientY - moveElemRect.top; //鼠标按下时和选中元素的坐标偏移:y坐标
        }
          
      }
  });

  //监听鼠标放开事件
  document.addEventListener('mouseup', function(e) {
          let moveX = e.clientX - tLeft, 
                moveY = e.clientY - tTop;
          
          moveElem.style.left = moveX + 'px';
          moveElem.style.top = moveY + 'px';
      dragging = false;

  });

  //监听鼠标移动事件
  document.addEventListener('mousemove', function(e) {
      let moveX = e.clientX - tLeft, 
                moveY = e.clientY - tTop;
          console.log(moveX,moveY);
  });
  })

</script>
  
<style scope>
.tage {
  margin: 0 auto;
  background-color: #2f4554;
  display: flex;
  flex-direction: column;
}
.img {
  width: 100px;
  /* position:absolute; */
  margin-left: 20px;
}
</style>