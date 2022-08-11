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
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SidebarNav",
  props:['employee'],
  methods:{
    searchEmployee(e){
        console.log(e.target.value)
    }
  }
};
</script>
