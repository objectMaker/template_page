<template>
    <div class="payment_container_border">
      <div class="payment_container">
        <div class="price_container">
          <div>2000 明细</div>
          <div>实付: ￥2000</div>
        </div>
        <div class="payment_btn">
          支付
        </div>
      </div>
    </div>
</template>

<script>
export default {
    data(){
        return {

        }
    }
}
</script>

<style lang="scss" scoped>
  .payment_container_border{
    border-top: 1px solid #e8e8ea;
  }
  .payment_container{
    display: flex;
    justify-content: space-between;
    height: 70px;
    width: 508px;
    margin-left: 23px;
    .price_container{
      line-height: 35px;
      div:nth-child(1){
        color: #fe2c55;
      }
      div:nth-child(2){
        color: black;
      }
    }
  }
  .payment_btn{
    width: 136px;
    margin-top: 7px;
    height: 54px;
    border-radius: 4px;
    line-height: 54px;
    background-color: #fe2c55;
    text-align: center;
    color: white;
    font-size: 22px;
  }
</style>