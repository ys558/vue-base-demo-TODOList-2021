<template>
  <header>
    <h1>{{ title }}</h1>
    <!-- 11. 绑定改动按钮文字 -->
    <!-- 12. Button组件复用，改 @toggle-add-task 为 @btn-click -->
    <Button 
    :text="showAddTask ? 'Close': 'Add Task'" 
    :color="showAddTask ? 'red' : 'green' "
    @btn-click="$emit('toggle-add-task')" 
    />
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
    title: String,
    showAddTask: Boolean
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