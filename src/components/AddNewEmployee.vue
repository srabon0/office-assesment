<template>
  <div>
    <div class="d-flex m-3 justify-content-between">
      <h1 v-if="editRequest?.editreq">{{ head2 }}</h1>
      <h1 v-else>{{ head1 }}</h1>
      <button
        @click="createNew"
        v-if="editRequest?.editreq"
        class="btn btn-sm btn-success fw-bold"
      >
        Create New
      </button>
    </div>
    <div class="border border-2 rounded">
      <form class="m-2 p-3" v-if="editRequest?.editreq" @submit.prevent="updateEmployee">
        <div class="row g-3">
          <span> {{ editRequest?.id }} </span>
          <div class="col">
            <input
              type="text"
              class="form-control"
              placeholder="Employee Name"
              aria-label="Employee Name"
              :value="editRequest?.name"
              v-on:input="setUpdateName"
              required
            />
          </div>

          <div class="col">
            <input
              type="text"
              class="form-control"
              placeholder="Employee Address"
              aria-label="Employee Address"
              :value="editRequest?.address"
              v-on:input="setUpdateAddress"
              required
            />
          </div>
        </div>
        <input
          v-if="editRequest?.editreq"
          type="submit"
          value="Edit Employee"
          class="btn btn-primary my-3"
        />
      </form>
      <form v-else class="m-2 p-3" @submit.prevent="addNewEmployee">
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
  </div>
</template>

<script>
export default {
  name: "OfficeAssesmentAddNewEmployee",

  data() {
    return {
      newName :"",
      newAddress :"",
      updateUserId:this.editRequest?.id,
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
    createNew() {
      this.$emit("createNew");
    },
    setUpdateName(e){
      this.newName = (e.target.value)
    },
    setUpdateAddress(e){
      this.newAddress = (e.target.value)
    },
    updateEmployee(){
      var updatedValue =  {
        userId:this.editRequest.id,
        newName:this.newName,
        newAdd:this.newAddress
      }
      this.$emit("updateUser", updatedValue)
    }
  },
};
</script>

<style lang="scss" scoped></style>
