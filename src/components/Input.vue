<template>
  <div class="form-group">
    <label>{{ label }}</label>
    <input
      :id="id"
      type="text"
      :label="label"
      :name="name"
      class="form-control"
      :class="{'is-invalid': this.error}"
      v-model="text"
      required
    />
    <span class="form-error" v-if="this.error">{{message}}</span>
    <!-- <p>{{errorSubmit}}</p> -->
  </div>
</template>

<script>
export default {
  name: "Input",
  props: ["id", "value", "label", "name", "message", "errorSubmit"],
  data() {
    return {
      ids: this.id,
      text: this.value,
      error: false,
      errorSubmits: this.errorSubmit
    };
  },
  watch: {
    text: function(val) {
      if (val === "" || val === null) {
        this.error = true;
        this.$emit("inputValueEmit", val, this.ids);
      } else {
        this.error = false;
        this.errorSubmits = false;
        this.$emit("inputValueEmit", val, this.ids);
      }
    }
  },
  updated() {
    if (this.errorSubmits !== this.errorSubmit) {
      this.errorSubmits = this.errorSubmit;
      if ((this.errorSubmits && this.text === "") || this.text === null) {
        this.error = true;
      } else {
        this.error = false;
      }
    }
  }
};
</script>

<style scoped>
label {
  color: #292b2c;
  font-size: 16px;
  line-height: 2.7;
  margin-bottom: 0;
}

label:after {
  content: "*";
  color: red;
  margin-left: 4px;
}

input {
  padding: 10px 15px;
  border-radius: 5px;
  font-size: 16px;
  height: 50px;
}

.form-error {
  color: #dc3545;
  font-size: 14px;
}
</style>
