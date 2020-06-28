<template>
    <div class="tab-bar-item" @click="itemClick">
      <div v-if="!isActive" ><slot name="icon-item"></slot></div>
      <div v-else><slot name="icon-item-active"></slot></div>
      <div :style="activeStyle"><slot name="icon-text"></slot></div>
    </div>
</template>

<script>
  export default {
    name: "TabBarItem",
    props: {
      path: String,
      activeColor: {
        type: String,
        default: 'red'
      }
    },
    data() {
      return{

      }
    },
    computed: {
      isActive(){
        return !this.$route.path.indexOf(this.path);
      },
      activeStyle(){
        return this.isActive ? {color: this.activeColor} : {}
      }
    },
    methods: {
      itemClick(){
        this.$router.replace(this.path)
      }
    }
  }
</script>

<style scoped>
  .tab-bar-item{
    flex: 1;
    text-align: center;
    height: 49px;
  }
  .tab-bar-item img{
    width: 24px;
    height: 24px;
    margin-top: 3px;
    vertical-align: middle;
    margin-bottom: 2px;
  }
</style>