<template>
  <div class="border border-2 rounded">
    <form class="m-2 p-3" @submit.prevent="addNewEmployee">
      <div class="row g-3">
        <div class="col">
          <input
            v-model="name"
            type="text"
            class="form-control"
            placeholder="Employee Name"
            aria-label="Employee Name"
            required
          />
        </div>
        <div class="col">
          <input
            v-model="address"
            type="text"
            class="form-control"
            placeholder="Address"
            aria-label="Address"
            required
          />
        </div>
      </div>
      <input type="submit" value="Add New" class="btn btn-primary my-3" />
    </form>
  </div>
</template>

<script>
export default {
  name: "OfficeAssesmentAddNewEmployee",

  data() {
    return {
      name: "",
      address: "",
    };
  },

  mounted() {},

  methods: {
    addNewEmployee() {
      var newEmp = { name: this.name, address: this.address, checked:false };
      this.$emit("addEmployee", newEmp);
      this.name="",
      this.address=""
    

    },
  },
};
</script>

<style lang="scss" scoped></style>
