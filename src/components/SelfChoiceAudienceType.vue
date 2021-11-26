<template>
  <div class="self_choice_audience_type_bg">
    <div class="self_choice_option">
      <TopNav>
          <template #left>
            <div class="top_aside_words">
              取消
            </div>
          </template>
          <template #default>
            <div>
              自定义观众类型
            </div>
          </template>
          <template #right>
            <div class="top_confirm_btn top_aside_words">
              确认
            </div>
          </template>
      </TopNav>
      <div class="self_choice_bottom">

      </div>
    </div>
  </div>
</template>

<script>
import TopNav from "./TopNav";
export default {
  name:'SelfChoiceAudienceType',
  components:{
    TopNav,
  },
  data(){
    // 554 623
    return {
    }
  },
  methods:{

  }
}
</script>

<style lang="scss" scoped>
.self_choice_audience_type_bg{
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  width: 100%;
  background: rgba(0,0,0,.3);
  .self_choice_option{
    position: absolute;
    height: 623px;
    bottom: 0;
    width: 100%;
    //background-color: white;
    color: black;
    .top_confirm_btn{
      color: #fe2c55;
    }
    .top_aside_words{
      padding: 0 25px;
      font-size: 22px;
    }
    .self_choice_bottom{
      height: 552px;
      background-color: white;
    }
  }

}
</style>