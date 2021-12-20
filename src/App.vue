<template>
  <!-- <div class="vertical-center">
    
  </div> -->
  <!-- <router-view v-if="falsy"/> -->
  <login v-if="loginValid" />
  <home
    v-if="homeValid"
    @logOut="LogOut"
    :student="student"
    :requests="generalRequests"
    @upvote="upVote"
    @downvote="downVote"
    @addReq="makeReq"
  />
</template>

<script>
// import Router from "./router/index.js";
import Login from "./components/Login.vue";
import home from "./components/Home.vue";
export default {
  components: { Login, home },
  data() {
    return {
      counter: 0,
      test: "test",
      student: null,
      loginValid: true,
      homeValid: false,
      students: [
        {
          name: "دارا سارایی",
          user: "9799999",
          pass: "1234",
          reqs: [],
        },
        {
          name: "سارا دارایی",
          user: "9899999",
          pass: "1234",
          reqs: [],
        },
      ],
      generalRequests: [
        // {
        //   key: 0,
        //   type: "اضافه ظرفیت",
        //   date: new Date().toLocaleDateString("fa-IR"),
        //   courseName: "پیشرفته",
        //   valid: true,
        //   applicant: [],
        // },
        // {
        //   key: 1,
        //   type: "تغییر ساعت",
        //   date: new Date().toLocaleDateString("fa-IR"),
        //   courseName: "پیشرفته",
        //   valid: true,
        //   applicant: [],
        // },
      ],
      privateRequests: [],
    };
  },
  computed: {},
  provide() {
    return {
      student: this.student,
      voorood: this.vorood,
      request: this.generalRequests,
      privateReqs: this.privateRequests,
      generalReqs: this.generalRequests,
    };
  },
  methods: {
    upVote(id, user) {
      const req = this.generalRequests.find((req) => req.key == id);
      if (!req.applicant.includes(user)) {
        req.applicant.push(user);
      } else {
        alert("درخواست شما قبلا ثبت شده !");
      }
    },
    downVote(id, user) {
      const req = this.generalRequests.find((req) => req.key == id);
      if (req.applicant.includes(user)) {
        req.applicant.pop(user);
      } else {
        alert("درخواستی از سمت شما وجود ندارد !");
      }
    },
    makeReq(type, name, user) {
      const newReq = {
        key: this.generalRequests.length,
        type: type,
        date: new Date().toLocaleDateString("fa-IR"),
        courseName: name,
        valid: true,
        applicant: [user],
      };
      this.generalRequests.push(newReq);
    },

    toggleLoginValid() {
      this.loginValid = !this.loginValid;
    },
    toggleHomeValid() {
      this.homeValid = !this.homeValid;
    },

    LogOut() {
      this.toggleLoginValid();
      this.toggleHomeValid();
      this.student = null;
    },

    vorood(user, pass) {
      const stdn = this.students.find(
        (std) => std.user == user && std.pass == pass
      );

      if (stdn) {
        this.student = stdn;
        // Router.push({ name: "home", params: { std } });
        this.toggleLoginValid();
        this.toggleHomeValid();
      } else {
        alert("نام کاربری یا رمز عبور اشتباه است!");
      }
    },
  },
};
</script>

<style>
body {
  background-color: #44a1a0;
}
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #44A1A0;
}

#nav a.router-link-exact-active {
  color: #42b983; */
/* } */
</style>
