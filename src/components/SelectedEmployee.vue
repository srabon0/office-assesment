<template>
  <div>
    <div v-if="selectedEmp.length" >
      <table class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">
            Name
            <button @click="sortByName" class="btn btn-sm btn-outline-dark ms-4 cursor-pointer">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="16"
                height="16"
                fill="currentColor"
                class="bi bi-sort-alpha-down"
                viewBox="0 0 16 16"
              >
                <path
                  fill-rule="evenodd"
                  d="M10.082 5.629 9.664 7H8.598l1.789-5.332h1.234L13.402 7h-1.12l-.419-1.371h-1.781zm1.57-.785L11 2.687h-.047l-.652 2.157h1.351z"
                />
                <path
                  d="M12.96 14H9.028v-.691l2.579-3.72v-.054H9.098v-.867h3.785v.691l-2.567 3.72v.054h2.645V14zM4.5 2.5a.5.5 0 0 0-1 0v9.793l-1.146-1.147a.5.5 0 0 0-.708.708l2 1.999.007.007a.497.497 0 0 0 .7-.006l2-2a.5.5 0 0 0-.707-.708L4.5 12.293V2.5z"
                />
              </svg> Sort </button>
          </th>
          <th scope="col">Address
            <button @click="sortByAdd" class="btn btn-sm btn-outline-dark ms-4 cursor-pointer">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="16"
                height="16"
                fill="currentColor"
                class="bi bi-sort-alpha-down"
                viewBox="0 0 16 16"
              >
                <path
                  fill-rule="evenodd"
                  d="M10.082 5.629 9.664 7H8.598l1.789-5.332h1.234L13.402 7h-1.12l-.419-1.371h-1.781zm1.57-.785L11 2.687h-.047l-.652 2.157h1.351z"
                />
                <path
                  d="M12.96 14H9.028v-.691l2.579-3.72v-.054H9.098v-.867h3.785v.691l-2.567 3.72v.054h2.645V14zM4.5 2.5a.5.5 0 0 0-1 0v9.793l-1.146-1.147a.5.5 0 0 0-.708.708l2 1.999.007.007a.497.497 0 0 0 .7-.006l2-2a.5.5 0 0 0-.707-.708L4.5 12.293V2.5z"
                />
              </svg> Sort by Address </button>
          </th>
          <th scope="col">Action</th>
        </tr>
      </thead>
      <SelectedEmployeeRow
        @editUser="onEditUser"
        @deleteUser="onDeleteUser"
        :selectedEmp="selectedEmp"
      ></SelectedEmployeeRow>
    </table>
    <Pagination @setPage="onSetPage" :pageCount="pageCount" ></Pagination>
    </div>
    <div v-else><h3 class="text-danger">Sorry no Data</h3></div>
  </div>
</template>

<script>
import SelectedEmployeeRow from "./SelectedEmployeeRow.vue";
import Pagination from "./Pagination.vue";
export default {
  name: "OfficeAssesmentSelectedEmployee",
  props: ["selectedEmp","pageCount"],
  data() {
    return {
    
    };
  },
  computed: {
  },
  mounted() {},
  methods: {
    sortByName: function () {
      this.$emit("sortByName");
    },
    sortByAdd(){
      this.$emit("sortByAdd")
    },
    onDeleteUser(user) {
      this.$emit("deleteUser", user);
    },
    onEditUser(user) {
      this.$emit("editUser", user);
    },
    onSetPage(pageNumber){
      this.$emit("setPage",pageNumber)
    }
  },
  components: { SelectedEmployeeRow, Pagination },
};
</script>

<style lang="scss" scoped></style>
