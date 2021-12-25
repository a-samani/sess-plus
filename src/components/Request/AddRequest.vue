<template>
  <form
    @submit.prevent
    action="/action_page.php"
    style="direction: rtl; margin-top: 30px; margin-right: 40px"
  >
    <label for="cars" style="margin-left: 10px">موضوع :</label>
    <select name="cars" id="cars" v-model="type">
      <option value="azafeZarfiat">{{ ezafe }}</option>
      <option value="azafeZarfiatSpc">{{ ezafeSpc }}</option>
      <option value="examTimeChange">{{ examTimeChange }}</option>
      <option value="classTimeChange">{{ classTimeChange }}</option>
      <option value="kharejBakhsh">{{ kharejBakhsh }}</option>
      <option value="darsArshad">{{ Arshad }}</option>
      <option value="grayesh">{{ grayesh }}</option>
    </select>

    <div style="overflow: auto;height:400px;direction: rtl">
      <component :is="componentId" v-bind="componentProps"></component>
    </div>
    <br /><br />
    <!-- <label style="margin-left: 10px">نام درس :</label>
    <input type="text" v-model="courseName" />
    <br />

    <button
      type="submit"
      value="Submit"
      style="margin-top: 30px; margin-right: 40px"
      @click="sendReqData"
    >
      ثبت درخواست
    </button> -->
  </form>
  <!-- <button @click="TesT">test</button> -->
</template>

<script>
import ReqArshadGrayesh from "./options/ReqArshadGrayesh.vue";
import ReqChangeClassTime from "./options/ReqChangeClassTime.vue";
import ReqChangeExamTime from "./options/ReqChangeExamTime.vue";
import ReqDarsArshad from "./options/ReqDarsArshad.vue";
import ReqDarsBaksh from "./options/ReqDarsBaksh.vue";
import ReqZarfiat from "./options/ReqZarfiat.vue";
import ReqZarfiatSpc from './options/ReqZarfiatSpc.vue'

export default {
  components: {
    ReqArshadGrayesh,
    ReqChangeClassTime,
    ReqChangeExamTime,
    ReqDarsArshad,
    ReqDarsBaksh,
    ReqZarfiat,
    ReqZarfiatSpc
  },
  props: ["student"],
  emits: ["add-request"],
  data() {
    return {
      ezafe: "اضافه ظرفیت عمومی",
      ezafeSpc: "اضافه ظرفیت اختصاصی",
      examTimeChange: "تغییر ساعت امتحان",
      classTimeChange: "تغییر ساعت کلاس",
      kharejBakhsh: "برداشتن درس از بخش های دیگر",
      Arshad: "برداشتن درس ارشد",
      grayesh: "برداشتن درس از گرایش دیگر *مخصوص دانشجویان ارشد*",
      courseName: "",
      type: "",
    };
  },
  methods: {
    // TesT() {
    //   alert(this.student.name);
    // },
    sendReqData() {
      if (this.courseName == "" || this.type == "") {
        alert("لطفا اطلاعات را تکمیل کنید");
      } else {
        this.$emit("add-request", this.type, this.courseName);
        alert("درخواست ثبت شد!");
        (this.courseName = ""), (this.type = "");
      }
    },
  },
  computed: {
    componentId() {
      switch (this.type) {
        case "azafeZarfiat":
          return ReqZarfiat;

        case "grayesh":
          return ReqArshadGrayesh;

        case "darsArshad":
          return ReqDarsArshad;

        case "kharejBakhsh":
          return ReqDarsBaksh;

        case "classTimeChange":
          return ReqChangeClassTime;

        case "examTimeChange":
          return ReqChangeExamTime;

        case "azafeZarfiatSpc":
          return ReqZarfiatSpc;
        default:
          return null;
      }
    },
    componentProps() {
      return {
        student: this.student,
        type: this.type,
        studentReqs : this.student.reqs
      };
    },
  },
};
</script>
