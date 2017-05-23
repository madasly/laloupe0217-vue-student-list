<script>
import axios from 'axios';
import StudentLine from './StudentLine';
import AddStudent from './studentInfo';


export default {
  components: {
    StudentLine,
    AddStudent,
  },
  data() {
    return {
      students: [],
    };
  },
  methods: {
    getAll() {
      axios.get('/students')
      .then((response) => {
        this.students = response.data;
      });
    },
    AddStudent(student) {
      axios.post('/students', student)
      .then((res) => {
        this.students.push(res.data);
      });
    },
    remove(index) {
      axios.delete(`/students/${this.students[index].id}`).then(() => {
        this.students.splice(index, 1);
      });
    },
  },
  mounted() {
    this.getAll();
  },
};
</script>

<template>

  <div>
    <student-line v-for='(student, index) in students' :student="student" v-on:remove="remove(index)"> </student-line>
  </div>
</template>

<style>
</style>
