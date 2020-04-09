<template>
      <!-- 用变量控制按钮左右类名 -->
      <button class="diy-button" :class="{[`icon-${iconPosition}`]:true}" @click="$emit('click')">    
        <!-- 判断是否传入icon值 -->
        <diy-icon class="icon" v-if="name && loading == false" :name="`${name}`"></diy-icon>
        <!-- 加载中动画按钮 -->
        <diy-icon v-if="loading" :class="`loading icon`" :name="`loading`"></diy-icon>
        <div class="content">
          <slot />
        </div>
      </button>
</template>

<script>
export default {
  props:{
    icon:{},
    name:{},
    loading:{
      type: Boolean,
      default: false
    },
    iconPosition:{
      type:String,
      default:'left',
      // 属性检查器：获取用户传入的icon值并判断是否合法
      validator(value){
        return !(value !== 'left' && value !== 'right'); 
      }
    }
  },
  data () {
    return {

    }
  },
  components:	{},
  methods: {

  },
}
</script>

<style lang="less" scoped>
//  加载中动画
  @keyframes load {
    0%{ transform: rotate(360deg); }
    100%{ transform: rotate(0deg); }
  }
  .diy-button{
    font-size: var(--font-size);
    height: var(--button-height);
    padding: 0 1em;
    /* 继承父元素字体 */
    font: inherit;
    border-radius: var(--border-radius);
    border: 1px solid var(--border-color);
    background: var(--button-bg);
    display: inline-flex;
    justify-content: center;
    align-items: center;
    vertical-align: middle;
    /deep/.icon{
      height: 1.3em;
      width: 1.3em;
      order: 1;
      margin-right: .02em;
    }
    .content{
      order: 2;
    }
  }
  .diy-button:hover{
    border-color: var(--border-color-hover);
  }
  .diy-button:active{
    background: var(--button-active-bg);
  }
  .diy-button:focus{
    outline: none;
  }
  // 图标在右边的样式
  .icon-right{
    /deep/.icon{
      order: 2;
      margin-right: 0;
      margin-left: .02em;
    }
    .content{
      order: 1;
    }
  }

  .loading{
    height: 1.35em;
    width: 1.35em;
    animation:load 2s infinite linear;
  }

</style>