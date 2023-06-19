<template>
    <div>
      <form>
        <div>
          <label>Lesson:</label>
          <input type="text" v-model="lesson"/>
        </div>
        <div>
          <label>Date:</label>
          <input type="date" v-model="date"/>
        </div>
        <button @click="addLesson">Add Lesson</button>
      </form>
      <ul>
        <li v-for="(lesson, index) in lessons" :key="index">
          {{ lesson.topic }} - {{ lesson.date }}
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        lesson: '',
        date: '',
        lessons: []
      }
    },
    methods: {
      addLesson() {
        this.lessons.push({
          topic: this.lesson,
          date: this.date
        })
        this.lesson = ''
        this.date = ''
        localStorage.setItem('lessons', JSON.stringify(this.lessons))
      }
    },
    mounted() {
      if (localStorage.getItem('lessons')) {
        this.lessons = JSON.parse(localStorage.getItem('lessons'))
      }
    }
  }
  </script>
  
  <style>
    /* LessonView component styles */
    form {
      margin-bottom: 20px;
    }
  </style>
  