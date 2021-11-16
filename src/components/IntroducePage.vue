<template>
    <div class="container">
     <TopNav>
       <template #left>
         <div></div>
       </template>
       <template #right>
         <div></div>
       </template>
     </TopNav>
      <div class="bottom_container">
        <div class="pic_container">
        </div>
        <div class="question">
          <span class="weight">DOU+</span>是什么？
        </div>
        <div class="answer">
          直播间导流工具，能够在你直播期间，为你带来更多观众。
        </div>
        <div class="no_show">
          <div >
          </div>
          <div>
            不再显示
          </div>
        </div>
        <div class="btn_container">
          <div class="btn">
            立即加热
          </div>
        </div>
      </div>
      <div class="divide">
      </div>
    </div>
</template>

<script>
import TopNav from "@/components/TopNav";
export default {
    name:'IntroducePage',
  components:{
    TopNav,
  },
    data(){
        return {
        }
    }
}
</script>

<style lang="scss" scoped>
  .container{
    z-index: 99;
    height: 714px !important;
    background-color: white !important;
    border-top-left-radius: 12px;
    border-top-right-radius: 12px;
    width: 100%;
    color: black !important;
    .bottom_container{
      width: 508px;
      margin-left: 23px;
      margin-top: 23px;
      .pic_container{
        background-color: orange;
        height: 326px;
      }
      .question{
        margin-top: 35px;
        font-size: 25px;
        .weight{
          font-weight: 600;
        }
      }
      .answer{
        margin-top: 20px;
        font-size: 19px;
        font-weight: 400;
        color: #a1a2a6;
      }
      .no_show{
        margin-top: 42px;
        overflow: hidden;
        div{
          line-height: 23px;
          font-size: 19px;
          vertical-align: top;
          float: left;
        }
        div:nth-child(1){
          height: 22px;
          width: 22px;
          border: 2px solid #e3e3e4;
          border-radius: 50%;
        }
        div:nth-child(2){
          margin-left: 16px;
          color: #575757;
        }
      }
      .btn_container{
        padding-top: 30px;
        .btn{
          height: 66px;
          text-align: center;
          color: white;
          font-size: 23px;
          background-color: #fe2c55;
          line-height: 66px;
          border-radius: 2px;
        }
      }
    }
    .divide{
      position: absolute;
      height: 1px;
      width: 100%;
      background-color: #e8e8ea;
      bottom: 97px;
    }
  }
</style>