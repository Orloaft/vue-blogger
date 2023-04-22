<template>
    <div>
    
      <form onSubmit="preventDefault">  <input v-model="newTask"  placeholder="Add a task"><button @click="addTask">add</button></form>

      <ul>
        <li v-for="(task, index) in tasks" :key="index" style="text-decoration: {{task.completed ? none:line-through}};">
          <input type="checkbox" v-model="task.completed" @change="completeTask(task)">
          {{ task.text }}
          <button @click="removeTask(index)">Remove</button>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
import { looseIndexOf } from '@vue/shared'

  export default {
    data() {
      return {
        newTask: '',
        tasks: [],
      }
    },
    methods: {
      addTask() {
        if (this.newTask.trim() === '') return
        this.tasks.push({
          text: this.newTask.trim(),
          completed: false,
        })
        this.newTask = ''
      },
      removeTask(index) {
        this.tasks.splice(index, 1)
      },
      completeTask(task) {
        
        this.tasks[this.tasks.indexOf()].completed = true;
      },
    },
  }
  </script>
 
  