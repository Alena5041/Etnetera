<template>
  <div>
    <ul>
      <TaskItem
        v-for="(item, i) of items"
        :item="item"
        :key="i"
        v-bind:index="i"
        v-on:remove-task="removeTask"
        v-on:start-edit-task="startEditTask"
        v-on:finish-edit-task="finishEditTask"
      />
    </ul>
  </div>
</template>

<script>
import TaskItem from './TaskItem.vue'
export default {
  name: 'TaskList',
  components: {
    TaskItem
  },
  props: {
    items: {
      type: Object,
      required: true
    },
  },
  methods: {
    removeTask(id) {
      this.$emit('remove-task', id)
    },
    startEditTask(item) {
      this.$emit('start-edit-task', item)
    },
    finishEditTask(item, editedTitle) {
      this.$emit('finish-edit-task', item, editedTitle)
    }
  }
}
</script>
