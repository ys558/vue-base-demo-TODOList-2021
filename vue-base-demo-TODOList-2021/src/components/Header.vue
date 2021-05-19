<template>
  <header>
    <Button text="Add Task" color="green" />
  </header>
</template>

<script>
import Button from './Button'

export default {
  name: 'Header',
  // 2. 父子组件传值：props接收：
  // props也可写成，不进行类型检验：
  // props: ['text', 'color',],

  props: {
    text: String, 
    color: String,
  },
  components: {
    Button
  } 
}
</script>

<style scoped>
  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
  }
</style>