<template>
  <div>
    <form>
      <div>
        <label>Name:</label>
        <input type="text" v-model="name"/>
      </div>
      <div>
        <label>Grade:</label>
        <input type="text" v-model="grade"/>
      </div>
      <button @click="addStudent">Add Student</button>
    </form>
    <ul>
      <li v-for="(student, index) in students" :key="index">
        {{ student.name }} - {{ student.grade }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      grade: '',
      students: []
    }
  },
  methods: {
    addStudent() {
      this.students.push({
        name: this.name,
        grade: this.grade
      })
      this.name = ''
      this.grade = ''
      localStorage.setItem('students', JSON.stringify(this.students))
    }
  },
  mounted() {
    if (localStorage.getItem('students')) {
      this.students = JSON.parse(localStorage.getItem('students'))
    }
  }
}
</script>

<style>
  /* StudentCard component styles */
  form {
    margin-bottom: 20px;
  }
</style>
