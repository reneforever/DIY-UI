<template>
  <div class="wrapper" :class="`ok`">
    <!-- 绑定常用事件并支持v-model -->
      <input class="diy-input" type="text" :value="value" :disabled="disabled" :readonly="readonly"
      @change="$emit('change',$event.target.value)"
      @input="$emit('input',$event.target.value)"
      @focus="$emit('focus',$event.target.value)"
      @blur="$emit('blur',$event.target.value)"
      >
      <template v-if="error">
        <icon class="diy-icon" name="error"></icon>
        <span>{{error}}</span>
      </template>
      <template v-if="ok">
        <icon class="diy-icon" name="ok"></icon>
      </template>
  </div>
</template>

<script>
import Icon from '../icon/icon'
export default {
  props:{
    value:{
      type: String
    },
    disabled:{
      type: Boolean,
      default: false
    },
    readonly:{
      type: Boolean,
      default: false
    },
    error:{
      type: String 
    },
    ok:{
      type: Boolean
    }
  },
  data () {
    return {

    }
  },
  components:	{Icon},
  methods: {},
}
</script>

<style lang="less" scoped>
  .wrapper{
    display: inline-block;
    vertical-align: middle;
    .diy-input{
      height: 2.7em;
      font-size: 12px;
      border: 1px solid var(--border-color);
      border-radius: var(--border-radius);
      padding: 2px 8px;
    }
    .diy-input:hover{
      border-color: #666;
    }
    .diy-input:focus{
      outline: none;
      box-shadow: inset 0 1px 3px rgba(0,0,0,0.5);
    }
    .diy-input:disabled,.diy-input:read-only{
      border-color: #aaa;
      color: #aaa;
      // 更改鼠标样式
      cursor: not-allowed;
    }
  }
  .error{
    // 错误时出现的错误信息和设置icon
      .diy-input{
        border-color: #c0392b;
      }
      .diy-icon{
      position: absolute;
      margin-top: 9px;
      margin-left: 2px;
      width: 15px;
      height: 15px;
    }
      span{
        font-size: 12px;
        margin-left: 24px;
        color: #c0392b;
      }
    }
    .ok{
      .diy-input{
        border-color: #2ecc71;
      }
      .diy-icon{
      position: absolute;
      margin-top: 9px;
      margin-left: 2px;
      width: 15px;
      height: 15px;
    }
  }
</style>