<template>
  <div class="col-3 bg-dark" id="sticky-sidebar">
    <div class="sticky-top">
      <div class="nav flex-column">
        <h1 class="text-white fs-3">Employee List</h1>
        <div class="input-group mb-3">
          <span class="input-group-text" id="inputGroup-sizing-default"
            >Name</span
          >
          <input
            placeholder="Search..."
            type="text"
            class="form-control"
            aria-label="Sizing example input"
            aria-describedby="inputGroup-sizing-default"
            v-on:input="searchEmployee"
          />
        </div>
        <table class="table table-dark table-striped">
          <thead>
            <tr>
              <th scope="col">#</th>
              <th scope="col">First</th>
              <th scope="col"></th>
              <th scope="col">Handle</th>
            </tr>
          </thead>
          <tr :key="emp.id" v-for="(emp, index) in searchResultIn">
            <th scope="row">{{ index + 1 }}</th>
            <td colspan="2">{{ emp.name }}</td>

            <td>
              <div>
                <input
                  class="form-check-input mt-0"
                  type="checkbox"
                  :value="emp.id"
                  @change="check(index)"
                  aria-label="Checkbox for following text input"
                />
              </div>
            </td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SidebarNav",
  data() {
    return {
      selectedEmployee: {},
    };
  },
  props: ["employee", "searchResultIn"],
  methods: {
    searchEmployee(e) {
      var keyword = e.target.value;
      this.$emit("searchEmployeeInList", keyword);
    },
    check(emp) {
      this.$emit("selectEmp", emp);
    },
  },
};
</script>