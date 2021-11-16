<template>
    <div class="payment_page_container">
      <TopNav/>
      <div class="wrapper">
          <div class="content">
<!--            分割线-->
            <div class="divide"></div>
<!--            预估-->
            <div class="back_white">
              <div class="content_top">
                <div class="content_top_left">
                  <div>预估带来互动数</div>
                  <div>实际效果与直播质量有关</div>
                </div>
                <div class="content_top_right">
                  1000-6000次
                </div>
              </div>
              <!--            下单金额-->
              <div class="paymentMoney">
                <div class="tips">
                  请选择下单金额
                </div>
                <div class="money_container">
                  <div class="money_item" v-for="(item,index) in moneyList" :class="index===answer.money?'active':''" :key="index">
                    {{item}}
                  </div>
                </div>
              </div>
              <div class="paymentMoney">
                <div class="tips">
                  你更在意 <i class="iconfont icon-wenhaofuhao-"></i>
                </div>
                <div class="money_container">
                  <div class="money_item" v-for="(item,index) in noticeList" :class="index===answer.notice?'active':''" :key="index">
                    {{item}}
                  </div>
                </div>
              </div>
              <div class="paymentMoney">
                <div class="tips">
                  你想吸引的观众类型
                </div>
                <div class="money_container">
                  <div class="appeal_audience_type" v-for="(item,index) in audienceTypeList" :class="index===answer.audienceType?'active':''" :key="index">
                    {{item}}
                  </div>
                </div>
              </div>
              <div class="paymentMoney">
                <div class="tips">
                  选择加热方式 <i class="iconfont icon-wenhaofuhao-"></i>
                </div>
                <div class="money_container">
                  <div class="appeal_audience_type" v-for="(item,index) in hotLiveRoomTypeList" :class="index===answer.hotLiveRoomType?'active':''" :key="index">
                    {{item}}
                  </div>
                </div>
              </div>
              <div class="rightHotLiveRoom" v-if="answer.hotLiveRoomType === 0">
                <div class="left_explain">
                  期望曝光时长<i class="iconfont icon-wenhaofuhao-"></i>
                </div>
                <div class="addTime">
                  <i class="iconfont icon-jianshaojianqujianhao"></i>
                  <div>
                    {{answer.time}}小时
                  </div>
                  <i class="iconfont icon-zengjiatianjiajiahao"></i>
                </div>
              </div>
              <div class="rightHotLiveRoom">
                <div class="left_explain">
                  <i class="iconfont icon-wenhaofuhao-"></i> 优惠券
                </div>
                <div class="not_coupon">
                  无可用优惠券 <i class="iconfont icon-wenhaofuhao-"></i>
                </div>
              </div>
              <div class="agreement_container">
                <div class="top_line">
                  点击支付则视为同意
                  <span class="agreement_color">
                    DOU+服务协议
                  </span>
                  和
                  <span class="agreement_color">
                    DOU+币服务协议
                  </span>
                </div>
                <div class="down_line">
                  直播结束后，未完成的购买曝光量会折算对应金额退回DOU+账户。可在「我」-「更多功能」-「DOU+上热门」里查看
                </div>
              </div>
            </div>
<!--            最后的预估-->
            <div class="pre_judge">
              <i class="iconfont icon-fire color_active"></i>
              预估带来
              <span class="color_active">
                1000~6000
              </span>
              互动数
            </div>
          </div>
      </div>
      <Payment class="payment"/>
    </div>
</template>

<script>
import Payment from "./Payment";
import TopNav from "./TopNav";
import BScroll from '@better-scroll/core'
import ScrollBar from '@better-scroll/scroll-bar'
export default {
  name:'PaymentPage',
  components:{
    Payment,
    TopNav,
  },
    data(){
        return {
          moneyList:[
              '2000',
              '5000',
              '10000',
              '自定义',
          ],
          noticeList:[
            '直播间人气',
            '直播间涨粉',
            '观众打赏',
            '观众互动',
          ],
          audienceTypeList:[
              '系统智能推荐',
              '自定义观众类型',
          ],
          hotLiveRoomTypeList:[
            '直接加热直播间',
            '选择视频加热直播间',
          ],
          answer:{
            money:0,
            notice:0,
            audienceType:1,
            hotLiveRoomType:0,
            time:0.5,
          }
        }
    },
  mounted() {
    this.$nextTick(()=>{
      BScroll.use(ScrollBar)
      new BScroll('.wrapper', {
        // ...... 详见配置项
        mouseWheel: true,
        ScrollBar:false,
      })
    })
  }
}
</script>

<style lang="scss" scoped>
.payment_page_container{
  position: relative;
  background-color: white;
  border-top-left-radius: 12px;
  border-top-right-radius: 12px;
  height: 700px;
  width: 100%;
  .payment{
    position: absolute;
    bottom: 0;
    width: 100%;
  }
  .wrapper{
    height: 560px;
    overflow: hidden;
    background-color: #f8f8f8;
    color: black;
    .divide{
      height: 16px;
    }
    .content_top{
      display: flex;
      justify-content: space-between;
      width: 508px;
      margin-left: 23px;
      height: 116px;
      border-bottom: 1px solid #e3e3e4;
      .content_top_left{
        height: 80px;
        line-height: 40px;
        font-size: 19px;
        margin-top: 18px;
        div:nth-child(1){
          font-size: 23px;
        }
        div:nth-child(2){
          color: #9fa0a5;
        }
      }
      .content_top_right{
        line-height: 116px;
        font-size: 31px;
        color: #fe2c55;
      }
    }
    .paymentMoney{
      width: 508px;
      margin-left: 23px;
      border-bottom: 1px solid #e3e3e4;
      height: 144px;
      overflow: hidden;
      .tips{
        margin-top: 22px;
        font-size: 19px;
        color: #9fa0a5;
      }
      .money_container{
        display: flex;
        margin-top: 15px;
        justify-content: space-between;
        .money_item{
          width: 118px;
          height: 50px;
          line-height: 50px;
          font-size: 19px;
          text-align: center;
          border: 1px solid #e3e3e4;
        }
        .appeal_audience_type{
          width: 246px;
          height: 50px;
          line-height: 50px;
          font-size: 19px;
          text-align: center;
          border: 1px solid #e3e3e4;
        }
        .active{
          background-color: #fff3f5;
          border: 1px solid #ffe9ed;
          color: #fd6e8b;
        }
      }
    }
    //直接加热直播间
    .rightHotLiveRoom{
      display: flex;
      justify-content: space-between;
      width: 508px;
      margin-left: 23px;
      font-size: 19px;
      height: 85px;
      line-height: 85px;
      border-bottom: 1px solid #e3e3e4;
      .iconfont{
        font-size: 23px;
        color: #9fa0a5;
      }
      .left_explain{
      }
      .addTime{
        display: flex;
        width: 220px;
        justify-content: space-around;
      }
      .not_coupon{
        color: #9fa0a5;
      }
    }
    //同意用户协议
    .agreement_container{
      width: 508px;
      margin-left: 23px;
      font-size: 18px;
      color: #9fa0a5;
      .agreement_color{
        color: #386ea4;
      }
      .top_line{
        padding: 16px 0 28px;
      }
      .down_line{
        padding-bottom: 48px;
      }
    }
    .pre_judge{
      height: 60px;
      line-height: 60px;
      width: 508px;
      margin-left: 23px;
      font-size: 19px;
      .color_active{
        color: #fe2c55;
        font-size: 19px;
      }
    }
    .back_white{
      background: white;
    }
  }
}

</style>