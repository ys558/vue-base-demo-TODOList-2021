<template>
  <!-- 
    3. :style 样式绑定
    4. @click 或 v-on 事件绑定
   -->
  <button
    :style="{ background: color }"
    @click="onClick()"
    class="btn">{{ text }}</button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    text: String, color: String
  },
  // 4.
  methods:{
    onClick() {
      // 10.
      // 12. 复用 Button组件：改'toggle-add-task' 为 'btn-click'
      // this.$emit('toggle-add-task')
      this.$emit('btn-click')
    }
  },

}
</script>

<style>

</style>