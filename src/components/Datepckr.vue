<template>
  <div class="form-group">
    <label>{{ label }}</label>
    <date-picker
      v-model="date"
      value-type="format"
      format="MM/DD/YYYY"
      placeholder="Select Date"
      name="date-1558421606243"
      @change="dateValueToParent"
    ></date-picker>
  </div>
</template>

<script>
import DatePicker from "vue2-datepicker";
import "vue2-datepicker/index.css";

export default {
  name: "Datepckr",
  props: ["label"],
  components: { DatePicker },
  data() {
    return {
      date: null
    };
  },
  methods: {
    dateValueToParent(val) {
      this.$emit('dateValueEmit', val)
    }
  }
};
</script>

<style scoped>
.mx-datepicker {
  display: flex;
}
</style>
