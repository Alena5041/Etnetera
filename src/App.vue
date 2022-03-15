<template>
  <div id="app" class="card">
    <div class="card-header">
      <HeaderImg
        :taskDone="taskDone"
      />
      <h1>Tasks</h1>
    </div>
    <div class="card-body">
      <AddTask
        @add-task="addTask"
      />
      <TaskList
        :items="items"
        @remove-task="removeTask"
        @start-edit-task="startEditTask"
        @finish-edit-task="finishEditTask"
      />
    </div>
  </div>
</template>

<script>
import TaskList from './components/TaskList.vue'
import AddTask from './components/AddTask.vue'
import HeaderImg from './components/HeaderImg.vue';

export default {
  name: 'App',
  components: {
    TaskList, AddTask, HeaderImg
  },
  data() {
    return {
      items: [
        { id: 1, title: 'First', editing: false },
        { id: 2, title: 'Second', editing: false },
        { id: 3, title: 'Third', editing: false }
      ],
      taskDone: false
    }
  },
  methods: {
    removeTask(id) {
      this.items = this.items.filter(t => t.id !== id)
      this.taskDone = true;
      setTimeout(()=>{
        this.animationFinish()
      },1500);
    },
    animationFinish() {
      this.taskDone = false;
    },
    addTask(item) {
      this.items.push(item);
    },
    startEditTask(item) {
      item.editing = true;
    },
    finishEditTask(item, editedTitle) {
      item.editing = false;
      item.title = editedTitle;
    }
  }
}
</script>
