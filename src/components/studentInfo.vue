<script>
export default {
  data() {
    return {
      newStudent: {
        firstname: '',
        name: '',
        age: '',
      },
    };
  },
  props: ['student'],
  methods: {
    addStudent() {
      this.$emit('add-student,this.newStudent');
    },
  },
};
</script>

<template lang="pug">
div
  input(v-model="newStudent.lastname", placeholder="LASTNAME")
  input(v-model="newStudent.name", placeholder="NAME")
  input(v-model="newStudent.age", placeholder="AGE")
  button(@click="addstudent") Ajouter
</template>

<style>
</style>
