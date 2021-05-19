<template>
  <!-- 
    5. v-for: 数组循环
    6. 数据绑定，须要加 :key
  -->
  <div v-for="task in tasks" :key="task.id">
    <!-- 
      7. 事件派发，'delete-task'从子组件Task来，继续 $emit 传给父组件：
      8. 
    -->
    <Task :task="task" @delete-task="$emit('delete-task', task.id)" 
      @toggle-reminder="$emit('toggle-reminder', task.id)"
    />
  </div>
</template>

<script>
import Task from './Task'

export default {
  name: 'Tasks',
  props: {
    tasks: Array // or []
  },
  components: {
    Task
  },
  // 7. 事件派发 $emit 需要在这里注册，否则控制台会警告
  // 8. 
  emits: ['delete-task', 'toggle-reminder'],
}
</script>

<style>

</style>