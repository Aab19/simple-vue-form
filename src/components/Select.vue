<template>
  <div class="form-group">
    <label>{{ label }}</label>
    <select
      :id="id"
      class="form-control"
      v-model="gender"
      @change="selectOptionValueToParent"
      name="select-1558421554950"
    >
      <option value="male">Male</option>
      <option value="female">Female</option>
    </select>
  </div>
</template>

<script>
export default {
  name: "Select",
  props: ["id", "label"],
  data() {
    return {
      gender: "male"
    };
  },
  methods: {
    selectOptionValueToParent(e) {
      this.$emit('selectValueEmit', e.target.value)
    }
  }
};
</script>

<style scoped>
select {
  padding: 10px 15px;
  height: 50px;
  border-radius: 5px;
}
</style>
