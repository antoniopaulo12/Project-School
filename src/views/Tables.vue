<template>
  <div class="py-4 container-fluid">
    <div class=" row">
      <div class="col-12">
        <students-List />
      </div>
    </div>
  </div>
</template>

<script>
import studentsList from "./students/studentList.vue";

export default {
  name: "Estudiantes",
  components: {
    studentsList
  }
};
</script>
