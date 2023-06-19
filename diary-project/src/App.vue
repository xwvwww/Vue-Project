<template>
  <div>
    <LessonView />
    <Grading />
    <StudentCard />
  </div>
</template>

<script>
import LessonView from './components/LessonView.vue'
import Grading from './components/StudentGrading.vue'
import StudentCard from './components/StudentCard.vue'

export default {
  components: {
    LessonView,
    Grading,
    StudentCard
  }
}
</script>

<style>
  /* Common styles */
  form {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
  }
  form > div {
    margin: 10px 0;
  }
  label {
    font-weight: bold;
    margin-right: 10px;
  }
  input {
    padding: 10px;
  }
  button {
    padding: 10px 20px;
    background-color: lightgray;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
</style>
