<template>
  <div class="form-group">
    <label>{{ label }}</label>
    <div v-for="option in options" :key="option.value" class="custom-control custom-radio">
      <input
        type="radio"
        :id=option.id
        :name=name
        class="custom-control-input"
        @change="optionValueToParent"
        :value=option.value
      />
      <label class="custom-control-label" :for=option.id>{{option.label}}</label>
    </div>
  </div>
</template>

<script>
export default {
  name: "Selectopt",
  props: ["label", "name", "options"],
  methods: {
    optionValueToParent(e) {
      this.$emit('optionValueEmit', e.target.value)
    }
  }
};
</script>

<style scoped>
.custom-control-label {
  font-weight: 400;
}

.custom-control-input:checked ~ .custom-control-label::before {
  background-color: #fed136;
  border-color: #fed136;
}
</style>
