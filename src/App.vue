<template>
  <div id="app">
    <Code/>
    <Pic :clip_left="clip_left" />
    <div class="hover" ref="drag" :style="{left:this.left}" @mousedown="startDrag($event)" ><i class="fa fa-arrows-h"></i></div>
  </div>
</template>

<script>

import Code from "@/components/CODE";
import Pic from "@/components/PIC";
export default {
  name: 'App',
  components: {Code, Pic},
  data(){
    return {
      clip_left:'0px',
      startX:0,
      startLeft:0,
      left:0,
      newLeft:0,
      last_clip_left:0
    }
  },
  mounted: function () {
    this.startLeft = document.body.clientWidth / 10 - 20;
    this.left = this.startLeft + 'px';
    console.log(this.startLeft);
    console.log(this.left);
  },
  watch:{
    newLeft(newVal,oldVal){
      this.startLeft -= oldVal;
      this.startLeft += newVal;
      this.left = (this.startLeft+this.last_clip_left) + 'px';
      this.clip_left = (this.newLeft +this.last_clip_left)+ 'px';
    }
  },
  methods:{
    startDrag(e){
      this.startX = e.clientX;
      this.$refs.drag.addEventListener('mousemove', this.onDrag);
      this.$refs.drag.addEventListener('mouseup', this.endDrag);
      this.$refs.drag.addEventListener('mouseleave', this.endDrag);
    },
    onDrag:function (e) {
      this.newLeft =  e.clientX - this.startX;
    },
    endDrag:function () {
        let x = this.clip_left.indexOf('p');
        this.last_clip_left = parseInt(this.clip_left.substr(0,x));
        this.$refs.drag.removeEventListener('mousemove', this.onDrag);
        this.$refs.drag.removeEventListener('mouseup', this.endDrag);
        this.$refs.drag.removeEventListener('mouseleave', this.endDrag);
    },
  }
}
</script>

<style lang="scss" rel="stylesheet/scss">
  @import "src/common/scss/mixins";
  @media (max-width: 1500px){
    #app{
      .hover{
        display: none !important;
      }
    }
  }
  #app {
    background-color: orange;
    width: 100vw;
    height: 100vh;
    position: relative;
    .hover{

      width: 40px;
      height: 40px;
      position: absolute;
      top: 50%;
      z-index: 9999;
      color: white;
      border-radius: 50%;
      background-color: orange;
      @include flexBox(center,center);
      transform: translateY(-50%);
      cursor: col-resize;
    }
  }
</style>
