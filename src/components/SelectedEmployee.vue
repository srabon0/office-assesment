<template>
  <div>
    <table v-if="selectedEmp.length" class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Name <span @click="sortByName"> Sort </span></th>
          <th scope="col">Address</th>
          <th scope="col">Action</th>
        </tr>
      </thead>
      <SelectedEmployeeRow
        @editUser="onEditUser"
        @deleteUser="onDeleteUser"
        :selectedEmp="selectedEmp"
      ></SelectedEmployeeRow>
    </table>
    <div v-else><h3 class="text-danger">Sorry no Data</h3></div>
  </div>
</template>

<script>
import SelectedEmployeeRow from "./SelectedEmployeeRow.vue";
export default {
  name: "OfficeAssesmentSelectedEmployee",
  props: ["selectedEmp"],
  data() {
    return {};
  },
  computed: {
    totalEmployee() {
      return this.selectedEmp?.length;
    },
  },
  mounted() {},
  methods: {
    sortByName: function () {
      console.log("Sort by name");
    },
    onDeleteUser(user) {
      this.$emit("deleteUser", user);
    },
    onEditUser(user) {
      this.$emit("editUser", user);
    },
  },
  components: { SelectedEmployeeRow },
};
</script>

<style lang="scss" scoped></style>
