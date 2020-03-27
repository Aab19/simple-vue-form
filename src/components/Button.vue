<template>
  <button type="button" class="btn btn-warning" :name="name" @click="clickEventToParent">
    {{ label }}
  </button>
</template>

<script>
export default {
  name: "Button",
  props: ["label", "name"],
  methods: {
    clickEventToParent() {
      this.$emit('clickEmit')
    }
  }
};
</script>

<style scoped>
.btn-warning {
  background-color: #fed136;
  border-color: #fed136;
  padding: 8px 48px;
  margin-top: 12px;
  text-transform: uppercase;
}
</style>
