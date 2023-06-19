<template>
    <div>
      <form>
        <div>
          <label>Topic:</label>
          <input type="text" v-model="topic"/>
        </div>
        <div>
          <label>Date:</label>
          <input type="date" v-model="date"/>
        </div>
        <button @click="addGrading">Add Grading</button>
      </form>
      <ul>
        <li v-for="(grading, index) in gradings" :key="index">
          {{ grading.topic }} - {{ grading.date }}
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        topic: '',
        date: '',
        gradings: []
      }
    },
    methods: {
      addGrading() {
        this.gradings.push({
          topic: this.topic,
          date: this.date
        })
        this.topic = ''
        this.date = ''
        localStorage.setItem('gradings', JSON.stringify(this.gradings))
      }
    },
    mounted() {
      if (localStorage.getItem('gradings')) {
        this.gradings = JSON.parse(localStorage.getItem('gradings'))
      }
    }
  }
  </script>
  
  <style>
    /* Grading component styles */
    form {
      margin-bottom: 20px;
    }
  </style>
  