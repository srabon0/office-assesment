<template>
  <div>
    <table class="table">
      <h1> Total Selected Employee : {{ totalEmployee }}</h1>
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Name</th>
          <th scope="col">Address</th>
          <th scope="col">Action</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th scope="row">1</th>
          <td>Mark</td>
          <td>Otto</td>
          <td>
            <div class="d-flex">
              <button class="btn btn-warning mx-1">Edit</button>
              <button class="btn btn-danger mx-1">Delete</button>
            </div>
          </td>
        </tr>
        <tr>
          <th scope="row">2</th>
          <td>Jacob</td>
          <td>Thornton</td>
          <td>
            <div class="d-flex">
              <button class="btn btn-warning mx-1">Edit</button>
              <button class="btn btn-danger mx-1">Delete</button>
            </div>
          </td>
        </tr>
        <tr>
          <th scope="row">3</th>
          <td colspan="2">Larry the Bird</td>
          <td>
            <div class="d-flex">
              <button class="btn btn-warning mx-1">Edit</button>
              <button class="btn btn-danger mx-1">Delete</button>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "OfficeAssesmentSelectedEmployee",
  props:['selectedEmp'],

  data() {
    return {};
  },
  computed:{
    totalEmployee(){
      return this.selectedEmp?.length
    }
  },

  mounted() {},

  methods: {},
};
</script>

<style lang="scss" scoped></style>
