<template>
  <div class="col" id="main">
    <AddNewEmployee @updateUser="onUpdateUser" @createNew="onCreateNew" :editRequest="editRequest"  @addEmployee="onAddnewEmployee"></AddNewEmployee>

    <div class="container my-3">
      <h3>Selected Employee list</h3>
      <SelectedEmployee
      
      @setPage="onSetPage"
        @editUser="onEditUser"
        @sortByName="onSortByName"
        @sortByAdd="onSortByAdd"
        @deleteUser="onDeleteUser"
        :selectedEmp="selectedEmp"
        :pageCount="pageCount"
      ></SelectedEmployee>
    </div>
  </div>
</template>

<script>
import AddNewEmployee from "./AddNewEmployee.vue";
import SelectedEmployee from "./SelectedEmployee.vue";
export default {
  components: { AddNewEmployee, SelectedEmployee },
  props: ["selectedEmp","editRequest","pageCount"],
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
    onCreateNew(){
      this.$emit("createNew")
    },
    onUpdateUser(user){
      this.$emit("updateUser",user)

    },
    onSortByName(){
      this.$emit("sortByName");
    },
    onSortByAdd(){
      this.$emit("sortByAdd")
    },
    onSetPage(pageNumber){
      this.$emit("setPage" , pageNumber)
    },
  },
};
</script>

<style></style>
