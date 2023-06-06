<template>
  <div>
    <div class="filter">
      <button
        @click="sortScore"
      >
        Sort by score
      </button>
      <button
        @click="filterScore(true)"
      >
        Show positive score
      </button>
      <button
        @click="filterScore(false)"
      >
        Show negative score
      </button>
      <button
        @click="reset"
      >
        Reset
    </button>
    </div>
    <div
      v-for="student in allStudents"
      :key="student.studentId"
      class="student_card"
    >
      <div
        v-for="key in keys"
        :key="key"
      >
        {{ key }}: {{ student[key] }}
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import Student from '@/types';

@Component
export default class StudentList extends Vue {
  @Prop() students!: Student[];

  public allStudents: Student[] = [];
  private sortDirection = "asc";
  public keys: string[] = [];

  mounted(): void {
    this.students ? this.reset() : [];
  }

  sortScore():void {
    this.allStudents?.sort((a,b) => this.sortDirection === "asc" ? a.score - b.score : b.score - a.score);
    this.sortDirection === "asc" ? this.sortDirection = "desc" : this.sortDirection = "asc";
  }

  filterScore(type: boolean): void {
    this.allStudents = this.students?.filter((item) => type ? item.score > 0 : item.score <= 0);
  }

  reset(): void {
    this.allStudents = [...this.students];
    this.keys = Object.keys(this.allStudents[0]);
    this.sortDirection = "asc";
  }
}
</script>

<style lang="scss">
  .filter {
    button {
      margin-right: 10px;
    }
  }
  
  .student_card {
    border: 1px solid #000;
    margin: 10px 0;
    padding: 10px;
  }
</style>