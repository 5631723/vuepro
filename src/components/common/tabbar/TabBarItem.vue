<template>

  <div class="tab-bar-item" @click="itemClick">
    <div v-if="!isActive">
      <slot name="item-icon"></slot>
    </div>
    <div v-else>
      <slot name="item-icon-actvie"></slot>
    </div>
<!--    <div :class="{active:isActive}">-->
    <div :style="activeStyle">
      <slot name="item-text"></slot>
    </div>

    <!--    <img slot="item-icon" src="../../assets/img/tabbar/home.svg" alt="">-->
    <!--    <div slot="item-text">首页</div>-->
  </div>


</template>

<script>
  export default {
    name: "TabBarItem",
    data() {
      return {
        // isActive: true
      }
    },
    computed: {
      isActive() {
        //活跃路由的path属性如果包含当前组件中的path属性文字
        return this.$route.path.indexOf(this.path) != -1;
      },
      activeStyle(){
        return this.isActive?{color:this.activeColor}:{};
      }
    },
    methods: {
      itemClick() {
        console.log(this.path);
        this.$router.push(this.path)
      }
    },
    props: {
      //由组件标签上的属性传入
      path: String,
      activeColor:{
        type:String,
        default:'red'
      }
    }
  }
</script>

<style scoped>

  .tab-bar-item {
    flex: 1;
    text-align: center;
    height: 49px;
    font-size: 14px;
  }

  .tab-bar-item img {
    height: 24px;
    width: 24px;
    vertical-align: middle;
    margin-top: 3px;
  }

  /*.active {*/
  /*  color: red;*/
  /*}*/

</style>
