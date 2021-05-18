<template>
<!-- 8. 和7类似 -->
  <div :class="[task.reminder ? 'reminder' : '', 'task']"
    @dblclick="$emit('toggle-reminder', id)"
  >
    <h3>
      {{ task.text }}
      <i @click="onDelete(task.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ task.day }}</p>
  </div>
</template>

<script>
export default {
  name: 'Task',
  props: {
    task: Object
  },
  methods: {
    onDelete(id) {
      // 7. this.$emit 事件派发，派发给父组件执行，传参函数名，参数
      this.$emit('delete-task', id)
    }
  }
}
</script>

<style>
.fas {
  color: red;
}
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.reminder {
  border-left: 5px solid green;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>