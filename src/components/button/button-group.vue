<template>
  <div class="button-group">
      <slot />
  </div>
</template>

<script>
export default {
  data () {
    return {

    }
  },
  components:	{},
  methods: {},
  mounted(){
    // 渲染时检查子元素格式是否合法，有错时提醒用户
    for(let node of this.$el.children){
      if(node.nodeName !== 'BUTTON'){
        console.warn('格式不正确，button-group中的元素必须是button')
      }
    }
  }
}
</script>

<style lang="less" scoped>
  .button-group{
    display: inline-flex;
    vertical-align: middle;
    .diy-button{
      border-radius: 0;
      :not(:first-child){
        // 解决边框不合并的问题
        margin-left: -1px;
      }
    }
    .diy-button:first-child{
      border-top-left-radius: var(--border-radius);
      border-bottom-left-radius: var(--border-radius);
    }
    .diy-button:last-child{
      border-top-right-radius: var(--border-radius);
      border-bottom-right-radius: var(--border-radius);
    }
    // hover时到顶层
    .diy-button:hover{
      position: relative;
      z-index: 1;
    }
  }
  
</style>