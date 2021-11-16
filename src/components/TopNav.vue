<template>
  <div class="top">
    <slot name="left">
      <div>
        <i class="iconfont icon-31fanhui1"></i>
      </div>
    </slot>
    <slot>
      <div>
        <span class="weight">DOU+</span>直播上热门
      </div>
    </slot>
    <slot name="right">
      <div>
        <i class="iconfont icon-wenhaofuhao-"></i>
      </div>
    </slot>
  </div>
</template>

<script>
export default {
  name:'TopNav',
    data(){
        return {
        }
    }
}
</script>

<style scoped lang="scss">
.top{
  background-color: white;
  border-top-left-radius: 12px;
  border-top-right-radius: 12px;
  height: 70px;
  display: flex;
  justify-content: space-between;
  color: black;
  font-size: 27px;
  line-height: 70px;
  border-bottom: 1px solid #e8e8ea;
  .weight{
    font-weight: 600;
  }
  .iconfont{
    font-size: 27px;
    margin: 0 20px;
  }
}
</style>