<template>
  <div id="app">
    <task v-bind:tasks="tasks"></task>
  </div>
</template>

<script>
import axios from 'axios'
import Task from './components/Task'

export default {
  name: 'App',
  components: {
    Task
  },
  data () {
    return {
      tasks: []
    }
  },
  mounted () {
    axios.get('/tasks')
      .then((response) => {
        console.log(response.data)
        this.tasks = response.data
      })
      .catch((err) => {
        console.log(err)
      })
  }
}
</script>
