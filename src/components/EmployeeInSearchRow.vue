<template>
  <tbody>
    <tr :key="emp.id" v-for="emp in employee">
      <th scope="row">{{ emp.id }}</th>
      <td colspan="2">{{ emp.name }}</td>

      <td>
        <div>
          <input
            class="form-check-input mt-0"
            type="checkbox"
            value=""
            aria-label="Checkbox for following text input"
          />
        </div>
      </td>
    </tr>
  </tbody>
</template>

<script>
export default {
  name: "OfficeAssesmentEmployeeInSearchRow",

  data() {
    return {};
  },
  props: ["searchResultIn", "employee"],

  mounted() {},

  methods: {},
};
</script>

<style lang="scss" scoped></style>
