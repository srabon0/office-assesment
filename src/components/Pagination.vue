<template>
<nav aria-label="Page navigation example">
  <ul class="pagination">
    <li style="cursor:pointer" @click="setPage(n)"  :key="i" v-for="(n, i) in pageCount" class="page-item"><a class="page-link">{{ n }}</a></li>
    
  </ul>
</nav>
</template>

<script>
export default {
  name: "OfficeAssesmentPagination",
  props: ["pageCount"],

  data() {
    return {
    };
  },

  methods: {
    setPage(pageNumber){
        this.$emit("setPage", pageNumber);
    }
  },
  computed: {
  },
};
</script>

<style lang="scss" scoped></style>
