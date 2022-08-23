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
          @setPage="onSetPage"
          @sortByName="onSortByName"
          @sortByAdd="onSortByAdd"
          @updateUser="onUpdateUser"
          @createNew="onCreateNew"
          @editUser="onEditUser"
          @deleteUser="onDeleteUser"
          @addEmployee="addNewEmp"
          :selectedEmp="selectedEmp"
          :editRequest="editRequest"
          :pageCount="pageCount"
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
        {
          id: 4,
          name: "Fokhrul Shipon",
          address: "Uttara, Dhaka",
          checked: false,
        },
        {
          id: 5,
          name: "Tanvir Ahmed",
          address: "Uttara, Dhaka",
          checked: false,
        },
        {
          id: 6,
          name: "Sehjad Saif",
          address: "Badda, Dhaka",
          checked: false,
        },
        {
          id: 7,
          name: "Ayesha Haque",
          address: "Dhanmondi, Dhaka",
          checked: false,
        },
        {
          id: 8,
          name: "Mofazzal Hossain",
          address: "Jatrabari, Dhaka",
          checked: false,
        },
        {
          id: 9,
          name: "Suraiya Islam Puspo",
          address: "Jatrabari, Dhaka",
          checked: false,
        },
        {
          id: 10,
          name: "Sayedd Anwar Jayed",
          address: "Banasree, Dhaka",
          checked: false,
        },
        {
          id: 11,
          name: "Mahmudul Hasan",
          address: "MohammadPur , Dhaka",
          checked: false,
        },
      ],
      //selectedEmp: [],
      searchResult: "",
      editRequest: null,
      sortByName: false,
      sortByAdd: false,
      currentPage: 0,
      maxPerPage: 5,
    };
  },
  methods: {
    onSetPage(pageNumber) {
      console.log("From App", pageNumber);
      this.currentPage = pageNumber;
    },
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
      user.editreq = true;
      this.editRequest = user;
    },
    onCreateNew() {
      return (this.editRequest = null);
    },
    onUpdateUser(user) {
      console.log(user);
      const updateEmployees = this.employee.map((emp) => {
        if (emp.id === user.userId) {
          return {
            ...emp,
            name: user.newName,
            address: user.newAdd,
            editreq: false,
          };
        }
        return emp;
      });
      this.employee = updateEmployees;
      this.editRequest = null;
    },
    onSortByName() {
      console.log("sort by name form the app");
      this.sortByAdd = false;
      this.sortByName = !this.sortByName;
    },
    onSortByAdd() {
      console.log("sort by Address form the app");
      this.sortByName = false;
      this.sortByAdd = !this.sortByAdd;
    },
    paginate(paginatedArray){
      const index = this.currentPage*this.maxPerPage
      console.log(index);
      return (paginatedArray.slice(index, index + this.maxPerPage))

    }
  },
  computed: {
    selectedEmp() {
      if (this.sortByName) {
        const temp = this.employee.filter((e) => e.checked);
        const sortedTemp =temp.sort((a, b) =>
          a.name.toLowerCase().localeCompare(b.name.toLowerCase())
        );
        return this.paginate(sortedTemp)
      }
      if (this.sortByAdd) {
        const temp = this.employee.filter((e) => e.checked);
        const sortedTemp = temp.sort((a, b) =>
          a.address.toLowerCase().localeCompare(b.address.toLowerCase())
        );
        return this.paginate(sortedTemp)
      } else {
        const temp =  this.employee.filter((e) => e.checked)
        return this.paginate(temp)
      }
    },
    // paginate: () => {
    //   if (this.currentPage >= this.pageCount) {
    //     this.currentPage = Math.max(0, this.pageCount - 1);
    //   }
    //   var index = this.currentPage * this.maxPerPage;
    //   console.log(index + " index");
    //   console.log(this.selectedEmp.slice(index, index + this.maxPerPage));
    //   return this.selectedEmp.slice(index, index + this.maxPerPage);
    // },

    sendEditReq() {
      return this.editRequest;
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
    pageCount() {
      let selectedEmployees = this.employee.filter((e) => e.checked)
      return Math.ceil(selectedEmployees.length / this.maxPerPage);
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
