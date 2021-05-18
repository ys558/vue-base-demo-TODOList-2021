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
      console.log('click')
    }
  },

}
</script>

<style>

</style>