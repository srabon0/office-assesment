<template>
  <div class="border border-2 rounded">
   <form class="m-2 p-3" action="">

     <div class="row g-3">
      <div class="col">
        <input
          type="text"
          class="form-control"
          placeholder="First name"
          aria-label="First name"
        />
      </div>
      <div class="col">
        <input
          type="text"
          class="form-control"
          placeholder="Last name"
          aria-label="Last name"
        />
      </div>
    </div>
    <input type="submit" value="Add New" class="btn btn-primary my-3" /> 
   </form>
  </div>
</template>

<script>
export default {
  name: "OfficeAssesmentAddNewEmployee",

  data() {
    return {};
  },

  mounted() {},

  methods: {},
};
</script>

<style lang="scss" scoped></style>
