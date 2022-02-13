<template>
  <div class="task-grid">
      <template v-if="tasks.length">
          <task v-for="(task, index) in tasks" :key="task.name" :task="task" @taskDeleted="$emit('taskDeleted', index)" @taskStateChanged="$emit('taskStateChanged', index)"></task>
      </template>
      <p  v-else class="no-task">No tasks pending</p>
  </div>
</template>

<script>
import Task from './Task.vue'
export default {
    components: {
        Task
    },
    props: {
        tasks: { type: Array, required: true }
    }
}
</script>

<style>
    .task-grid { /* refactor this to grid*/ 
        display: grid;
        justify-content: center;
        grid-row-gap: 10px;
        grid-template-columns: auto auto auto;
        position: relative;
        bottom: 70px;
    }
    .task-grid .task {
        margin: 10px;
    }

    .no-task {
        color: #aaa;
        font-size: 1.7rem;
    }
</style>