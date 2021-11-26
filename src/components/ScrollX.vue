<template>
    <div class="x_wrapper" ref="xwrapper">
      <div class="cont">
        <div class="item" v-for="(i,index) in 10" :key="i">
          <div class="item_active" v-if="index === 0">
          </div>
        </div>
      </div>
    </div>
</template>

<script>
import BScroll from '@better-scroll/core'
// import ScrollBar from '@better-scroll/scroll-bar'
export default {
    data(){
        return {
          scroll:'',
        }
    },
  mounted() {
    document.querySelectorAll('.cont')[0].style.width = document.querySelectorAll('.item').length*168+'px';
    console.log(document.querySelectorAll('.cont')[0].style.width)
  this.$nextTick(()=>{
    setTimeout(()=>{
      if (!this.scroll) {
        console.log('新建')
        this.scroll = new BScroll(this.$refs.xwrapper, {
          mouseWheel: true,
          scrollX: true,
          scrollY: false,
          stopPropagation: true,
        });
      } else {
        this.scroll.refresh();
      }
    },100)
  })
      // new BScroll('.wrapper', {
      //   // ...... 详见配置项
      //   mouseWheel: true,
      //   ScrollBar:false,
      //   scrollX:true,
      //   scrollY:false,
      //   stopPropagation: true,
      // })
  }
}
</script>

<style lang="scss" scoped>
    .x_wrapper{
      padding: 20px;
      height: 180px;
      overflow: hidden;
      .cont{
        display: flex;
        width: 200px;
        height: 100%;
        .item{
          width: 144px;
          margin: 0 10px;
          border-radius: 4px;
          flex-shrink: 0;
          height: 100%;
          background-color: gray;
          position: relative;
        }
        .item_active{
          position: absolute;
          box-sizing: border-box;
          width: 164px;
          height: 200px;
          left: -10px;
          top: -10px;
          border: 4px solid gold;
          background-color: transparent;
          border-radius: 8px;
        }
      }

    }
</style>