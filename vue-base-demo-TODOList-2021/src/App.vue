<template>
  <div class="container">
    <Header title="Task Tracker" />
    <AddTask @add-task='addTask' />
    <!-- 
      6. v-bind 或 : 数据绑定
      7. 将子组件 $emit 出来的事件进行绑定：
    -->
    <Tasks :tasks="tasks" @delete-task="deleteTask"
      @toggle-reminder="toggleReminder"
    />
  </div>
</template>

<script>
import Header from './components/Header'
import Tasks from './components/Tasks'
import AddTask from './components/AddTask'

export default {
  name: 'App',
  components: {
    // 1. 除了 import ,还需要在 components 属性里注册才能使用Component：
    Header, Tasks, AddTask
  },
  data() {
    return { 
      // 6. 数据绑定：
      tasks: []
    }
  },
  created() {
    this.tasks = [
      {id: 1, text: 'Doctor Appointment', day:'1st, Mar, 2:30pm', reminder: true},
      {id: 2, text: 'Meeting At School', day:'3rd, Mar, 1:30pm', reminder: false},
      {id: 3, text: 'Food Shopping', day:'3rd, Mar, 11:00pm', reminder: false},
    ]
  },
  methods: {
    // 7. 处理从子组件过来的事件：$emit
    deleteTask(id) {
      if (confirm('r u sure?')) this.tasks = this.tasks.filter( task => task.id !== id )
    },
    // 8.
    toggleReminder(id) {
      this.tasks = this.tasks.map(task => task.id === id ? {...task, reminder: !task.reminder } : task )
    },
    // 9.
    addTask(newTask) {
      this.tasks = [newTask, ...this.tasks,]
    },
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* { box-sizing: border-box; margin: 0; padding: 0; }
body { font-family: 'Poppins', sans-serif; }
.container { max-width: 500px; margin: 30px auto; overflow: auto; min-height: 300px; border: 1px solid steelblue; padding: 30px; border-radius: 5px;}
.btn { display: inline-block; background: #000; color: #fff; border: none; padding: 10px 20px; margin: 5px; border-radius: 5px; cursor: pointer; text-decoration: none; font-size: 15px; font-family: inherit;}
.btn:focus { outline: none; }
.btn:active { transform: scale(0.98);}
.btn-blcok { display: block; width: 100%; }

.task.reminder { border-left: 5px solid green; }
</style>
