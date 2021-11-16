<template>
    <div class="container">
<!--      顶部间距-->
      <div class="topDis">
      </div>
<!--      头部导航-->
      <div class="navBar">
        <div class="navItemContainer">
          <div class="navItem" v-for="(item,index) in navList" :key="index">
            <div :class="currentIndex === index?'active':''">{{item}}</div>
            <div v-show="currentIndex === index" class="whiteLine">
            </div>
          </div>
        </div>
        <div class="delete">
          <i class="iconfont icon-closel"></i>
        </div>
      </div>
<!--      中间推荐-->
      <div class="mid_push">
        <div class="sports_container">
          <div class="together">一起运动吧<i class="iconfont icon-bianji"></i></div>
          <div class="open_position">开启位置
            <i class="iconfont icon-arrow-right-copy-copy"></i>
          </div>
        </div>
        <div class="changeFace">
          更换封面
        </div>
        <div class="last_line">
          <div class="choose"><i class="iconfont icon-icmenu2"></i>选择直播内容</div>
          <div><i class="iconfont icon-huati"></i>选择话题</div>
        </div>
      </div>
      <div class="bottom_option">
        <div v-for="(item,index) in bottomOptionList" :key="index" class="option_item">
          <div class="icon">
            <i class="iconfont" :class="item.className"></i>
          </div>
          <div class="font">
            {{item.words}}
          </div>
        </div>
      </div>
      <div class="startLive">
        开始视频直播
      </div>
      <div class="bottom_nav">
        <div class="bottom_nav_item" v-for="(item,index) in bottomNavList" :key="index">
          <div>{{item}}</div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
    data(){
        return {
          currentIndex:0,
          navList:[
              '视频',
              '语音',
              '手游',
              '电脑',
          ],
          bottomOptionList:[
            {
              words:'翻转',
              className:'icon-jingtou-fanzhuan',
            },
            {
              words:'美化',
              className:'icon-meihua',
            },
            {
              words:'道具',
              className:'icon-daoju-heise',
            },
            {
              words:'商品',
              className:'icon-gouwuche',
            },
            {
              words:'游戏推广',
              className:'icon-airudiantubiaohuizhi-zhuanqu_youxi',
            },
            {
              words:'活动区',
              className:'icon-biaoqiankuozhan_huodong-247',
            },
            {
              words:'上热门',
              className:'icon-douyinremenshipin',
            },
            {
              words:'分享',
              className:'icon-59fenxiang',
            },
            {
              words:'设置',
              className:'icon-shezhi',
            },
            {
              words:'任务',
              className:'icon-renwu',
            },
          ],
          bottomNavList:[
              '分段拍',
              '快拍',
              '模板',
              '开直播',
          ],
          bottomChoose:3,
        }
    }
}
</script>

<style lang="scss">
  .container{
    width: 554px;
    height: 986px;
    background-color: #000;
    .topDis{
      height: 66px;
    }
    .navBar{
      position: relative;
      .navItemContainer{
        margin-left: 156px;
        display: flex;
        color: #717171;
        width: 244px;
        font-weight: 600;
        justify-content: space-between;
        font-size: 18px;
        .active{
          color: white;
        }
        .whiteLine{
          margin-top: 12px;
          height: 2px;
          background-color: white;
          width: 60%;
          margin-left: 20%;
          border-radius: 1px;
        }
      }
      .delete{
        color: white;
        position: absolute;
        left: 20px;
        top: 0;
        .iconfont{
          font-size: 30px;
        }
      }
    }

    .mid_push{
      position: relative;
      color: white;
      height: 566px;
      .sports_container{
        position: absolute;
        left: 190px;
        top: 35px;
        line-height: 34px;
        .together{
          font-size: 18px;
          font-weight: 600;
          .iconfont{
            margin-left: 2px;
          }
          .icon-bianji{
            font-weight: normal;
          }
        }
        .open_position{
          font-size: 15px;
        }
      }
      .changeFace{
        position: absolute;
        top: 86px;
        left: 121px;
        font-size: 12px;
        text-align: center;
        line-height: 16px;
      }
      .last_line{
        position: absolute;
        color: #a9a9a9;
        left: 112px;
        top: 119px;
        font-size: 14px;
        display: flex;
        width: 250px;
        justify-content: space-between;
        .iconfont{
          margin-right: 3px;
        }
      }
    }
    .bottom_option{
      color: white;
      display: flex;
      width: 325px;
      margin-left: 114px;
      flex-wrap: wrap;
      margin-top: -10px;
      .option_item{
        margin-top: 10px;
        height: 80px;
        width: 65px;
        text-align: center;
        .icon{
          .iconfont{
            font-size: 30px;
          }
        }
        .font{
          margin-top: 7px;
          font-size: 12px;
          color: #afafaf;
        }
      }
    }
    .startLive{
      color: white;
      background-color: #fe2c55;
      height: 56px;
      line-height: 56px;
      font-size: 20px;
      width: 300px;
      text-align: center;
      border-radius: 28px;
      margin-left: 128px;
    }
    .bottom_nav{
      color: #5f5f5f;
      display: flex;
      font-weight: 600;
      width: 343px;
      justify-content: space-around;
      margin-top: 40px;
      font-size: 21px;
    }
  }
</style>