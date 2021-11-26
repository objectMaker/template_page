<template>
    <div class="price_bg">

      <div class="price_input_container">
        <div class="close_line">
          <i class="iconfont icon-chacha1" @click="close"></i>
        </div>
        <div class="price_choice_type_top">
          自定义套餐
        </div>
        <div class="price_choice_type_bottom">
          预计带来观众<span class="audience_count">0</span>
        </div>
        <div>
          <input type="text" placeholder="请输入金额" class="self_input" >
        </div>
        <div class="price_explain">
          金额最低为200元
        </div>
        <div class="price_container_btn" :class="'price_container_btn_active'">
          确定
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name:'PriceDialog',
    data(){
        return {
        }
    },
  methods:{
    close(){
      this.$emit('closePriceDialog')
    }
  }
}
</script>

<style lang="scss" scoped>
    .price_bg{
      position: absolute;
      left: 0;
      top: 0;
      height: 100%;
      width: 100%;
      background: rgba(0,0,0,.3);

      .price_input_container{
        color: black;
        position: absolute;
        left: 50%;
        transform: translateX(-50%);
        top: 320px;
        height: 380px;
        width: 414px;
        background-color: white;
        border-radius: 4px;
        .close_line{
          padding: 0 15px;
          text-align: right;
          color: #a8a8a8;
          margin-top: 15px;
          .icon-chacha1{
            font-size: 30px;
          }
        }
        .price_choice_type_top{
          text-align: center;
          font-size: 27px;
          font-weight: 400;
        }
        .price_choice_type_bottom{
          display: flex;
          justify-content: center;
          line-height: 60px;
          height: 60px;
          .audience_count{
            margin-left: 14px;
            font-weight: bold;
            font-size: 23px;
          }
        }
        .self_input{
          position: relative;
          left: 50%;
          height: 60px;
          width: 356px;
          transform: translateX(-50%);
          border: none;
          outline: none;
          padding: 10px;
          box-sizing: border-box;
          background-color: #f1f1f2;
          color: black;
          border-radius: 4px;
          caret-color:#f8d336;
          font-size: 24px;
          &::-ms-input-placeholder{
            color: #bdbdc1;
          }
          &::-webkit-input-placeholder{
            color: #bdbdc1;
          }
        }
        .price_explain{
          position: relative;
          left: 50%;
          height: 50px;
          width: 356px;
          transform: translateX(-50%);
          font-size: 18px;
          line-height: 50px;
          color: #a7a8ad;
        }
        .price_container_btn{
          position: relative;
          left: 50%;
          height: 65px;
          width: 356px;
          transform: translateX(-50%);
          text-align: center;
          line-height: 65px;
          background-color: #fe96aa;
          color: white;
          font-size: 22px;
          font-weight: 400;
          border-radius: 4px;
          margin-top: 20px;
        }
        .price_container_btn_active{
          background-color: #fe2c55;
        }
      }
    }
</style>