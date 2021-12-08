<template>
  <div
    style="
      border: solid 1px black;
      display: flex;
      text-align: left;
      justify-content: center;
      flex-direction: column;
      margin : 0px;
    "
    class="nady"
  >
    <div class="inner-block" style="margin-left: 100px">
      <div class="vue-tempalte">
        <form @submit.prevent="">
          <h3>ورود به سیستم</h3>

          <div class="form-group">
            <label style="direction: rtl; float: right;margin-bottom: 10px">شماره دانشجویی :</label>
            <input
              type="num"
              class="form-control form-control-lg"
              v-model="user"
            />
          </div>

          <div class="form-group">
            <label style="direction: rtl; float: right;margin-bottom: 10px">رمز عبور : </label>
            <input
              type="password"
              class="form-control form-control-lg"
              v-model="pass"
            />
          </div>

          <button
            type="submit"
            class="btn btn-dark btn-lg btn-block"
            style="margin-top: 10px"
            @click="voorood(user, pass)"
          >
            ورود
          </button>
          <router-link to="home" style="margin-left: 5px"
            >فراموشی رمز عبور</router-link
          >
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  inject: ["voorood"],
  data() {
    return {
      user: "",
      pass: "",
    };
  },
  methods: {
    Login() {
      this.$emit("log-in", this.user, this.pass);
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  padding: 0px;
   
   
}

.nady {
  background-image: url("../assets/backed.jpg");
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-size: cover;
  height: 100vh;
  min-height: 100vh;
  display: flex;
  font-weight: 400;
  
}

body,
html,
.App,
.vue-tempalte,
.vertical-center {
  width: 100%;
  height: 100%;
}

.inner-block {
  width: 450px;
  margin: auto;
  background: #ffffff;
  box-shadow: 0px 14px 80px rgba(34, 35, 58, 0.2);
  padding: 40px 55px 45px 55px;
  border-radius: 15px;
  transition: all 0.3s;
}

.vertical-center {
  display: flex;
  text-align: left;
  justify-content: center;
  flex-direction: column;
}
body{
     background-color: #44a1a0;
}
</style>
