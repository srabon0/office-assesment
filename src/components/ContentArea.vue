<template>
  <div class="col" id="main">
          <h1>Add New Employee </h1>

          <AddNewEmployee @addEmployee="onAddnewEmployee"></AddNewEmployee>
         
          <div class="container my-3" >
            <h3> Selected Employee list </h3>
            <SelectedEmployee></SelectedEmployee>
          </div>
        </div>
</template>

<script>
import AddNewEmployee from './AddNewEmployee.vue';
import SelectedEmployee from './SelectedEmployee.vue';
export default {
    components: { AddNewEmployee, SelectedEmployee },
    methods:{
      onAddnewEmployee(emp){
        this.$emit("addEmployee", emp)
      }
    }
}
</script>

<style>

</style>