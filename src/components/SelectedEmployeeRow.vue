<template>
  <tbody>
   
    <tr :key="emp.id" v-for="(emp, index) in selectedEmp">
      <th scope="row">{{ index + 1 }}</th>
      <td>{{ emp.name }}</td>
      <td>{{ emp.address }}</td>
      <td>
        <div class="d-flex">
          <button class="btn btn-warning mx-1">Edit</button>
          <button class="btn btn-danger mx-1">Delete</button>
        </div>
      </td>
    </tr>
  </tbody>
</template>

<script>

export default {
  name: "OfficeAssesmentSelectedEmployeeRow",
  props: ["selectedEmp"],

  data() {
    return {}
  },

  methods: {

    
  },
};
</script>

<style lang="scss" scoped></style>
