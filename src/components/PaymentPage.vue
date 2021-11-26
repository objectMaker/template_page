<template>
    <div class="payment_page_container">
      <TopNav/>
      <div class="wrapper">
          <div class="content">
          <div class="hot_type_container">
            <div class="type_choose_line">你想要的加热方式</div>
            <div class="hot_type_item_container">
              <div class="add_hot_type" @click="changeHotType(index)" v-for="(item,index) in hotTypeList" :key="index" :class="answer.hotType===index?'active':''">
                <div class="hot_type_option">
                  <div>
                    {{item.type}}
                  </div>
                  <div class="gray_words">
                    <div>
                      {{item.lineOne}}
                    </div>
                    <div>
                      {{item.lineTwo}}
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
<!--            分割线-->
            <div class="divide"></div>
<div v-if="answer.hotType === 0">
  <!--            快速加热套餐-->
  <div class="price_explain">
    <div class="top_words">10分钟加热套餐 <i class="iconfont icon-wenhaofuhao-"></i></div>
    <div class="down_words">
      投放效果与直播质量相关，预估数据会上下浮动
    </div>
  </div>
  <!--            预计带来观众-->
  <div class="prejudge_audience">
    <div class="prejudge_item_container">
      <div class="prejudge_item" v-for="(item,index) in tenHotPriceList" :key="index">
        <div class="prejudge_title">预计带来观众</div>
        <div class="prejudge_range">
          {{item.audienceRange}}
        </div>
        <div class="prejudge_money">
          {{item.money}}
        </div>
      </div>
      <div class="prejudge_item" v-if="tenHotPriceList.length === 2"  @click="$emit('openPriceDialog')">
        <div class="top_icon">
          <i class="iconfont icon-bianji1"></i>
        </div>
        <div class="down_words">
          自定义
        </div>
      </div>
    </div>
    <div class="line_divide">

    </div>
  </div>
    <div :style="{backgroundColor:'white'}">
      <div class="rightHotLiveRoom">
        <div class="left_explain">
          <i class="iconfont icon-wenhaofuhao-"></i> 优惠券
        </div>
        <div class="not_coupon">
          无可用优惠券  <i class="iconfont icon-arrow-right-copy-copy"></i>
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
</div>
            <div v-else>
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
                    <div class="appeal_audience_type" @click="handleOpenSelfChoiceAudience(index)" v-for="(item,index) in audienceTypeList" :class="index===answer.audienceType?'active':''" :key="index">
                      {{item}}
                    </div>
                  </div>
                </div>
                <div class="paymentMoney">
                  <div class="tips">
                    选择加热方式 <i class="iconfont icon-wenhaofuhao-"></i>
                  </div>
                  <div class="money_container">
                    <div class="appeal_audience_type" v-for="(item,index) in hotLiveRoomTypeList"

                         :class="index===answer.hotLiveRoomType?'active':''" :key="index">
                      {{item}}
                    </div>
                  </div>
                </div>
                <div class="chooseVideoHotLiveRoom"  v-if="answer.hotLiveRoomType === 0">
                  <ScrollX></ScrollX>
                </div>
                <div class="rightHotLiveRoom">
                  <div class="left_explain">
                    期望曝光时长 <i class="iconfont icon-wenhaofuhao-"></i>
                  </div>
                  <div class="addTime">
                    <i @click="changeTime(false)" class="iconfont icon-jjian-"></i>
                    <div class="color_red">
                      {{answer.time}}小时
                    </div>
                    <i @click="changeTime(true)" class="iconfont icon-jia1 color_red"></i>
                  </div>
                </div>
                <div class="rightHotLiveRoom">
                  <div class="left_explain">
                    <i class="iconfont icon-wenhaofuhao-"></i> 优惠券
                  </div>
                  <div class="not_coupon">
                    无可用优惠券  <i class="iconfont icon-arrow-right-copy-copy"></i>
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
      </div>
      <Payment class="payment"/>
      <SelfChoiceAudienceType v-if="selfChoiceAudienceTypeVisible"/>
    </div>
</template>

<script>
import ScrollX from "./ScrollX";
import Payment from "./Payment";
import TopNav from "./TopNav";
import BScroll from '@better-scroll/core'
import ScrollBar from '@better-scroll/scroll-bar'
import SelfChoiceAudienceType from "./SelfChoiceAudienceType";
export default {
  name:'PaymentPage',
  components:{
    Payment,
    TopNav,
    ScrollX,
    SelfChoiceAudienceType,
  },
    data(){
        return {
          selfChoiceAudienceTypeVisible:true,
          bs:'',
          // 十分钟价格套餐列表
          tenHotPriceList:[
            {
              audienceRange:'100~600',
              money:200,
            },
            {
              audienceRange:'150~900',
              money: 300,
            }
          ],
          hotTypeList:[
            {
              type:'快速加热',
              lineOne:'迅速来人!',
              lineTwo:'PK、连麦好帮手',
            },
            {
              type:'自定义加热',
              lineOne:'精准投放!',
              lineTwo:'加热方式由你自定义',
            }
          ],
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
            audienceType:0,
            hotLiveRoomType:0,
            time:0.5,
            hotType:0,
          },

        }
    },
  methods:{
    handleOpenSelfChoiceAudience(index){
      this.answer.audienceType = index;
      if(index === 1){
        //打开自定义观众类型dialog
        this.selfChoiceAudienceTypeVisible = true;
      }
      console.log('111111111111111')
    },
    changeHotType(index){
        this.answer.hotType = index
        this.initBs()
    },
    initBs(){
      BScroll.use(ScrollBar)
      this.$nextTick(()=>{
        if(this.bs){
          this.bs.refresh()
        }else{
          this.bs = new BScroll('.wrapper', {
            // ...... 详见配置项
            mouseWheel: true,
            ScrollBar:false,
          })
        }

      })
    },
    changeTime(boolen){
      console.log('changetime')
      if(boolen){
        this.answer.time<24?this.answer.time+=0.5:'';
      }else{
        this.answer.time>0?this.answer.time-=0.5:'';
      }
    }
  },
  mounted() {
    this.initBs()
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
    height: 550px;
    overflow: hidden;
    background-color: #f8f8f8;
    color: black;
    .hot_type_container{
      padding: 0 23px;
      width: 508px;
      height: 250px;
      background-color: white;
      .type_choose_line{
        height: 88px;
        line-height: 88px;
        font-size: 25px;
      }
      .hot_type_item_container{
        display: flex;
        justify-content: space-between;
        .add_hot_type{
          width: 246px;
          height: 134px;
          border: 1px solid #e3e3e4;
          border-radius: 10px;
          box-sizing: border-box;
          padding: 18px;
          font-size: 20px;
          .gray_words{
            padding-top: 15px;
            line-height: 25px;
            font-size: 16px;
            color: #7c7d83;
          }
        }
        .active{
          background-color: #fff3f5;
          border: 1px solid #ffe9ed;
        }
      }
    }
    .divide{
      height: 16px;
    }
    .price_explain{
      height: 126px;
      width: 508px;
      padding:0 23px;
      background-color: white;
      .top_words{
        padding-top: 33px;
        padding-bottom: 14px;
        font-size: 24px;
      }
      .down_words{
        color: #7c7d83;
        font-size: 18px;
      }
    }
    .prejudge_audience{

      .prejudge_item_container{
        display: flex;
        width: 508px;
        padding:0 23px 20px;
        background-color: white;
        justify-content: space-between;
        .prejudge_item{
          width: 162px;
          height: 162px;
          border: 1px solid #e3e3e4;
          box-sizing: border-box;
          padding: 18px;
          border-radius: 12px;
          .prejudge_title{
            font-size: 18px;
            color: #7c7d83;
          }
          .prejudge_range{
            font-size: 23px;
            font-weight: 600;
            padding-top: 25px;
          }
          .prejudge_money{
            font-size: 20px;
            font-weight: 600;
            color: #fe2c55;
            padding-top: 25px;
          }
          .top_icon{
            text-align: center;
            .iconfont{
              font-size: 36px;
              color: #7c7d83;
            }
            padding: 16px 0;
          }
          .down_words{
            text-align: center;
            font-size: 26px;
          }
        }
      }
      .line_divide{
        height: 1px;
        background-color: #e3e3e4;
        width: 508px;
        margin-left: 23px;
      }
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
      min-height: 144px;
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
      .color_red{
        color: #fe2c55;
      }
      .left_explain{
      }
      .addTime{
        display: flex;
        width: 150px;
        justify-content: space-between;
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