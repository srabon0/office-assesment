<template>
  <div id="app">
    <div class="container-fluid">
      <div class="row">
        <SidebarNav v-bind:employee="employee"></SidebarNav>
        <ContentArea></ContentArea>
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
        },
        {
          id: 2,
          name: "Md Sohel Rana",
          address: "Mohammad Pur, Dhaka",
        },
      ],
    };
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
