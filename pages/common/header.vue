<template>
  <section>
    <!-- 顶部 -->
    <div class='topbox'>
      <div class='leftnav'>
        <img
          src="../../static/img/win.png"
          alt=""
          class='win'
        >
        <div class='text'>后台管理系统</div>
      </div>
      <div class='rightnav'>
        <img
          src="../../static/img/full.png"
          alt=""
          class='full'
        >
        <img
          src="../../static/img/radio.png"
          alt=""
          class='radio'
        >
        <img
          src="../../static/img/kudo.png"
          alt=""
          class='avater'
        >
        <div class='adminname' @click='isShowTab = !isShowTab;'>
                <span>admin</span>
                <img
                  src="../../static/img/down.png"
                  alt=""
                  class='down'
                >
              </div>
            </div>
      
         <transition name='fade'>
              <div class='display_box' v-show='isShowTab==true'>
                <div>切换账号</div>
                <div>退出登录</div>
              </div>
          </transition>
      </div>
    </div>

  </section>

</template>

<script>
import Logo from "~/components/Logo.vue";

export default {
  components: {

  },
  data() {
    return {
      isShow: "vContent",
      isShowTab: false
    };
  }
};
</script>

<style lang="scss">
// 引入公共css
@import '../../static/css/common';
/* 变量 */

$topBoxMargin: 15px;

/* */

// header
.topbox {
  background: #242f42;
  height: 70px;
  width: 100%;
  padding: 20px 20px;
  position: relative;
}
.win {
  width: 20px;
  display: inline-block;
  vertical-align: middle;
  margin-right: $topBoxMargin;
  cursor: pointer;
}
.text {
  color: #fff;
  font-size: 20px;
  display: inline-block;
  vertical-align: middle;
  font-weight: 700;
}
.full {
  width: 20px;
  display: inline-block;
  vertical-align: middle;
  margin-right: $topBoxMargin;
}
.radio {
  width: 20px;
  display: inline-block;
  vertical-align: middle;
  margin-right: $topBoxMargin;
}
.rightnav {
  position: absolute;
  right: 40px;
  top: 20px;
}
.avater {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  display: inline-block;
  vertical-align: middle;
  overflow: hidden;
  margin-right: $topBoxMargin;
}
.adminname {
  color: #fff;
  display:inline-block;
}
.down{
  display:inline-block;
  width:10px;
}
.left .el-tooltip__popper,
.right .el-tooltip__popper {
  padding: 8px 10px;
}
.isDisplay {
  display: block;
}
.display_box {
  z-index: 999;
  width: 100px;
  height: 50px;
  color: #ddd;
  border-radius: 5px;
  position: absolute;
  right: 20px;
  top: 60px;
  text-align:center;
  line-height: 25px;
  background: #324157;
  cursor:pointer;
}
/* 动画 */
/* 进入过渡后的状态以及离开过渡时的状态 */
.fade-enter-active, .fade-leave-active {
  transition: all .4s;
  height:50px;
  opacity: 1
}
/* 进入过渡前以及离开过渡后的状态 */
.fade-enter, .fade-leave-to{
  height: 0;
  opacity:0;
}
/* 媒体查询 */
@media screen and (max-width: 420px) {
  // 顶部
  $topBoxMargin: 10px;
  .topbox {
    font-size: 14px;
    height:50px;
    padding: 10px 20px;
  }
  .text {
    font-size: 14px;
  }
  .topbox img {
    width: 15px;
  }
  .win {
    margin-right: $topBoxMargin;
  }
  .full {
    margin-right: $topBoxMargin;
  }
  .radio {
    margin-right: $topBoxMargin;
  }
  .topbox .avater {
    margin-right: $topBoxMargin;
    width: 20px;
    height: 20px;
  }
  .rightnav {
    right: 10px;
    top:10px;
  }
  
}

@media screen and (max-width: 320px) {
  // 顶部
  $topBoxMargin: 5px;
  .topbox {
    font-size: 10px;
    height:40px;
    padding: 8px 15px;
  }
  .text {
    font-size: 10px;
  }
  .topbox img {
    width: 13px;
  }
  .win {
    margin-right: $topBoxMargin;
  }
  .full {
    margin-right: $topBoxMargin;
  }
  .radio {
    margin-right: $topBoxMargin;
  }
  .topbox .avater {
    margin-right: $topBoxMargin;
    width: 20px;
    height: 20px;
  }
  .rightnav {
    right: 5px;
    top:8px;
  }
  
}
//-- header end --//
</style>
