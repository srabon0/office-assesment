<template>
  <tbody>
    <tr :key="emp.id" v-for="(emp, index) in selectedEmp">
      <th scope="row">{{ index + 1 }}</th>
      <td>{{ emp.name }}</td>
      <td>{{ emp.address }}</td>
      <td>
        <div class="d-flex">
          <button class="btn btn-warning mx-1" @click="editUser(emp)">
            Edit
          </button>
          <button
            type="button"
            class="btn btn-danger"
            data-bs-toggle="modal"
            data-bs-target="#exampleModal"
            @click="employee = emp"
          >
            Delete
          </button>
        </div>
      </td>
    </tr>
    <DeleteModal @deleteUser="onDeleteUser" :emp="employee"></DeleteModal>
  </tbody>
</template>

<script>
import DeleteModal from "./DeleteModal.vue";
export default {
  name: "OfficeAssesmentSelectedEmployeeRow",
  props: ["selectedEmp"],
  data() {
    return {
      employee: {},
    };
  },
  methods: {
    onDeleteUser(user) {
      this.$emit("deleteUser", user);
    },
    editUser(emp) {
      this.$emit("editUser", emp);
    },
  },
  components: { DeleteModal },
};
</script>

<style lang="scss" scoped></style>
