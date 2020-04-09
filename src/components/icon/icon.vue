<template>
    <svg class="div-icon">
      <use :xlink:href="`#icon-${name}`"></use>
    </svg> 
</template>

<script>
export default {
  props:['name'],
  data () {
    return {

    }
  },
  components:	{},
  methods: {},
}
</script>

<style lang="less" scoped>
 .div-icon{
   width: 1.4em;
   height: 1.4em;
 }
</style>