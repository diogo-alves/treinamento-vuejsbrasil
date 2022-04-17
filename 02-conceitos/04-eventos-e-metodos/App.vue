<template>
	<div>
		<h1>Minha lista de tarefas</h1>
    <button @click="handleShowHideList()">Ver lista</button>
    <br>
    <input 
       type="text" v-focus
       v-model="currentTask"
       @keyup.enter="addTask()">

    <ul v-if="showList">
      <li v-for="(task, index) in tasks" 
          :key="`${task}-${index}`" 
          @dblclick="complete(task)"
          class="task-item" 
          :class="{ 'line-through': task.isDone }">
        {{ task.name }}
        <button @click="remove(task)">&times;</button>
      </li>
    </ul>
    <p v-else>Lista de tarefas escondida</p>
  </div>
</template>

<script>
  const focus = {
    inserted: (el) => {
      el.focus()
    }
  }

  export default {
    directives: {
      focus
    },
    data: () => ({
      currentTask: '',
      showList: false,
      tasks: [
        { name: 'Fazer o curso', isDone: false }
      ]
    }),
    methods: {
      addTask() {
        this.tasks.push({
          name: this.currentTask,
          isDOne: false
        })
        this.currentTask = ''
      },
      handleShowHideList() {
        this.showList = !this.showList
      },
      complete(task) {
        this.tasks  = this.tasks.map(t => {
          if (t.name === task.name) {
            return {...t, isDone: !t.isDone }
          }
          return { ...t }
        })
      },
      remove(task) {
        this.tasks = this.tasks.filter(t => t.name != task.name)
      }
    }
  }
</script>

<style scoped>
  .line-through {
    text-decoration: line-through;
  }
  .task-item {
    cursor: pointer;
  }
</style>