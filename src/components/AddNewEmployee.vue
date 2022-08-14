<template>
  <div>
    <div class="d-flex m-3 justify-content-between ">
      <h1 v-if="editRequest?.editreq">{{ head2 }}</h1>
      <h1 v-else>{{ head1 }}</h1>
      <button v-if="editRequest?.editreq" class="btn btn-sm btn-success fw-bold" >Create New </button>
    </div>
    <div class="border border-2 rounded">
      <form class="m-2 p-3" @submit.prevent="addNewEmployee">
        <div class="row g-3">
          <div>
            <div v-if="editRequest?.editreq" class="col">
              <input
                type="text"
                class="form-control"
                placeholder="Employee Name"
                aria-label="Employee Name"
                :value="editRequest?.name"
                required
              />
            </div>
            <div v-else class="col">
              <input
                v-model="name"
                type="text"
                class="form-control"
                placeholder="Employee Name"
                aria-label="Employee Name"
                required
              />
            </div>
          </div>
          <div>
            <div v-if="editRequest?.editreq" class="col">
              <input
                type="text"
                class="form-control"
                placeholder="Employee Address"
                aria-label="Employee Address"
                :value="editRequest?.address"
                required
              />
            </div>
            <div v-else class="col">
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
        </div>
        <input
          v-if="editRequest?.editreq"
          type="submit"
          value="Edit"
          class="btn btn-primary my-3"
        />
        <input
          v-else
          type="submit"
          value="Add New"
          class="btn btn-primary my-3"
        />
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "OfficeAssesmentAddNewEmployee",

  data() {
    return {
      name: "",
      address: "",
      head1: "Add New Employee",
      head2: "Edit Employee",
    };
  },
  props: ["editRequest"],

  computed: {},

  methods: {
    addNewEmployee() {
      var newEmp = { name: this.name, address: this.address, checked: false };
      this.$emit("addEmployee", newEmp);
      (this.name = ""), (this.address = "");
    },
  },
};
</script>

<style lang="scss" scoped></style>
