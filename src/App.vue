<template>
  <div id="app">
    <div class="container-fluid">
      <div class="row">
        <SidebarNav
          @searchEmployeeInList="onEmployeeSearch"
          @selectEmp="onEmployeeSelect"
          v-bind:searchResultIn="searchResultIn"
        ></SidebarNav>
        <ContentArea
          @editUser="onEditUser"
          @deleteUser="onDeleteUser"
          @addEmployee="addNewEmp"
          :selectedEmp="selectedEmp"
          :editRequest="editRequest"
        ></ContentArea>
        <div>{{ selectedEmp.length }}</div>
      </div>
    </div>
  </div>
</template>

<script>
import SidebarNav from "./components/SidebarNav.vue";
import ContentArea from "./components/ContentArea.vue";
export default {
  name: "App",
  components: {
    SidebarNav,
    ContentArea,
  },
  data() {
    return {
      employee: [
        {
          id: 1,
          name: "Md Amam Uddin Srabon",
          address: "House : 30, Road : 05, Dhaka",
          checked: false,
        },
        {
          id: 2,
          name: "Md Sohel Rana",
          address: "Mohammad Pur, Dhaka",
          checked: false,
        },
      ],
      //selectedEmp: [],
      searchResult: "",
      editRequest:null
    };
  },
  methods: {
    onEmployeeSearch(keyword) {
      console.log("In app", keyword);
      this.searchResult = keyword;
      console.log(this.employee);
    },
    addNewEmp(emp) {
      emp.id = this.employee.length + 1;
      this.employee.unshift(emp);
      console.log("from App in ", emp);
    },
    onEmployeeSelect(index) {
      this.employee[index].checked = !this.employee[index].checked;
    },
    onDeleteUser(user) {
      console.log("remove this ", user);
      const deletedList = this.employee.filter((e) => e.id !== user.id);
      this.employee = deletedList;
    },
    onEditUser(user) {
      console.log(user)
      user.editreq = true
      this.editRequest = user
    },
  },
  computed: {
    selectedEmp() {
      return this.employee.filter((e) => e.checked);
    },
    sendEditReq(){
      return this.editRequest
    },
    searchResultIn() {
      if (this.searchResult) {
        return this.employee.filter((item) => {
          return this.searchResult
            .toLowerCase()
            .split(" ")
            .every((v) => item.name.toLowerCase().includes(v));
        });
      } else {
        return this.employee;
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#sticky-sidebar {
  height: 100vh;
  padding: 10px;
}
</style>
