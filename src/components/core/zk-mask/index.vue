<template>
  <div class="zk-mask" :style="styles" component-path="core/zk-mask">
    <div class="">{{viewModel}}</div>
  </div>
</template>

<script>
  import { DIY_GETLINK_GET } from '@/service/api/apiUrl' // 引入Api接口常量
  import { editSetting } from './property'
  export default {
    name: editSetting.key,
    props: ['widgetDataId'],
    data () {
      return {
        viewModel: '', // 数据模型
        styles: {} // 可视化编辑样式
      }
    },
    mounted () {
      this.init()
    },
    methods: {
      async  init () {
        this.viewModel = await this.$api.get(DIY_GETLINK_GET, this.widgetDataId)
      }
    }
  }
</script>

<style scoped lang="less">
  @import '~_style/index.less'; // 颜色、边框、大小请使用assets/style/variable.less 和theme.less中的变量
  .zk-mask {
  	font-size: @font-size-base;
  }
</style>

