<template>
  <div id="app">
    <div class="container">
      <img class="logo" src="./assets/img/adeptforms.png" alt />
      <div class="row">
        <div class="col-6 offset-md-3">
          <div class="header-wrapper text-center">
            <h2>Register</h2>
            <h3>Please fill the form below to proceed next step.</h3>
          </div>
          <form>
            <Input
              id="username"
              label="User Name"
              v-on:inputValueEmit="inputValue"
              name="text-1558421438751"
              message="Username must be filled in."
              :value="form.username"
              :errorSubmit="error"
            />
            <Input
              id="password"
              label="Password"
              v-on:inputValueEmit="inputValue"
              name="text-1558421477780"
              message="Password must be filled in."
              :value="form.password"
              :errorSubmit="error"
            />
            <Input
              id="email"
              label="Email"
              v-on:inputValueEmit="inputValue"
              name="text-1558421492744"
              message="Email must be filled in."
              :value="form.email"
              :errorSubmit="error"
            />
            <Select id="gender" label="Gender" v-on:selectValueEmit="selectValue" />
            <Datepckr label="Date of Birth" v-on:dateValueEmit="dateValue" />
            <Selectopt
              label="Marital Status"
              name="radio-group-1558421657915"
              v-on:optionValueEmit="optionValue"
              :options="statusOptions"
            />
            <Button label="Save" v-on:clickEmit="submitForm" name="button-1558421848040" />
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Input from "./components/Input.vue";
import Select from "./components/Select.vue";
import Datepckr from "./components/Datepckr.vue";
import Selectopt from "./components/Selectopt.vue";
import Button from "./components/Button.vue";
import Data from "../data";

export default {
  name: "App",
  components: {
    Input,
    Select,
    Datepckr,
    Selectopt,
    Button
  },
  data() {
    return {
      submit: false,
      error: false,
      form: {
        username: null,
        password: null,
        email: null,
        gender: "male",
        date: null,
        status: null
      },
      statusOptions: [
        {
          id: "customRadio1",
          label: "Single",
          value: 1
        },
        {
          id: "customRadio2",
          label: "Married",
          value: 2
        },
        {
          id: "customRadio3",
          label: "Widowed",
          value: 3
        },
        {
          id: "customRadio4",
          label: "Divorced",
          value: 4
        }
      ]
    };
  },
  methods: {
    inputValue(val, id) {
      this.form[id] = val;
    },
    selectValue(val) {
      this.form.gender = val;
    },
    dateValue(val) {
      this.form.date = val;
    },
    optionValue(val) {
      this.form.status = val;
    },
    submitForm() {
      if (
        this.form.username &&
        this.form.password &&
        this.form.email &&
        this.form.date &&
        this.form.status !== null
      ) {
        this.submit = true;
        this.error = false;
        var store = Data;
        store.data = this.form;
        console.log(store);
        alert("Data saved successfully.");
        location.reload();
      } else if (
        this.form.username ||
        this.form.password ||
        this.form.email === null ||
        this.form.username ||
        this.form.password ||
        this.form.email === ""
      ) {
        this.submit = false;
        this.error = true;
      } else {
        this.error = false;
        this.submit = false;
      }

      if (!this.submit) {
        alert("All forms must be filled.");
      }
    }
  }
};
</script>

<style>
body {
  font-family: "Montserrat" !important;
  font-size: 14px;
  line-height: 1.3;
  color: #424143;
}

.logo {
  margin-top: 12px;
}

label {
  font-weight: bold;
}

.header-wrapper {
  margin-top: 24px;
}

.header-wrapper h3 {
  font-weight: 300;
  margin: 20px 0 24px;
}
.mx-calendar-content .cell.active {
  background-color: #fed136;
  color: #212529;
}
.mx-table-date .today {
  color: #fed136;
}

.mx-btn:hover {
  color: #fed136;
  border-color: #fed136;
}
</style>
