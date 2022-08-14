<template>
  <div class="col" id="main">
    <AddNewEmployee :editRequest="editRequest"  @addEmployee="onAddnewEmployee"></AddNewEmployee>

    <div class="container my-3">
      <h3>Selected Employee list</h3>
      <SelectedEmployee
        @editUser="onEditUser"
        @deleteUser="onDeleteUser"
        :selectedEmp="selectedEmp"
      ></SelectedEmployee>
    </div>
  </div>
</template>

<script>
import AddNewEmployee from "./AddNewEmployee.vue";
import SelectedEmployee from "./SelectedEmployee.vue";
export default {
  components: { AddNewEmployee, SelectedEmployee },
  props: ["selectedEmp","editRequest"],
  methods: {
    onAddnewEmployee(emp) {
      this.$emit("addEmployee", emp);
    },
    onDeleteUser(user) {
      this.$emit("deleteUser", user);
    },
    onEditUser(user) {
      this.$emit("editUser", user);
    },
  },
};
</script>

<style></style>
