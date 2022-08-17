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
        @sortByName="onSortByName"
        @sortByAdd="onSortByAdd"
        @updateUser="onUpdateUser"
        @createNew="onCreateNew"
          @editUser="onEditUser"
          @deleteUser="onDeleteUser"
          @addEmployee="addNewEmp"
          :selectedEmp="selectedEmp"
          :editRequest="editRequest"
        ></ContentArea>
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
        {
          id: 3,
          name: "Ikbal Nayeem",
          address: "Uttara, Dhaka",
          checked: false,
        },
      ],
      //selectedEmp: [],
      searchResult: "",
      editRequest:null,
      sortByName:false,
      sortByAdd:false,
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
      user.editreq = true
      this.editRequest = user
    },
    onCreateNew(){
      return this.editRequest = null;

    },
    onUpdateUser(user){
      console.log(user);
      const updateEmployees = this.employee.map(emp=>{
        if(emp.id===user.userId){
          return {...emp, name:user.newName,address:user.newAdd,editreq:false } ;
        }
        return emp;
      });
      this.employee = updateEmployees
      this.editRequest=null
    },
    onSortByName(){
      console.log("sort by name form the app")
      this.sortByAdd = false
      this.sortByName = !this.sortByName 

    },
    onSortByAdd(){
      console.log("sort by Address form the app")
      this.sortByName = false
      this.sortByAdd = !this.sortByAdd 
    },

  },
  computed: {
    selectedEmp() {
      if(this.sortByName){
         const temp = this.employee.filter((e) => e.checked);
         return temp.sort((a, b) => a.name.toLowerCase().localeCompare(b.name.toLowerCase()))
      }
      if(this.sortByAdd){
        const temp = this.employee.filter((e) => e.checked);
         return temp.sort((a, b) => a.address.toLowerCase().localeCompare(b.address.toLowerCase()))
      }
      else{
        return this.employee.filter((e) => e.checked);
        
      }
     
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
