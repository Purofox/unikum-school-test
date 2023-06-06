<template>
  <div id="app">
    <StudentList 
      :students="studentsList"
    />
  </div>
</template>

<script lang="ts">
  import { Component, Vue } from 'vue-property-decorator';
  import StudentList from '@/components/StudentList.vue';
  import Student from '@/types'

  @Component({
    components: {
      StudentList,
    },
  })

  export default class App extends Vue {
    
    studentsList: Student[] = [
      {
        firstName: 'Ivan',
        lastName: 'Petrov',
        studentId: 457856786,
        score: 100
      },
      {
        firstName: 'Petr',
        lastName: 'Ivanov',
        studentId: 78788463,
        score: 20
      },
      {
        firstName: 'Artem',
        lastName: 'Kotov',
        studentId: 45455,
        score: -150
      }
    ]
  }
</script>

<style lang="scss">
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
