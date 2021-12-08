<template>
  <form
    @submit.prevent
    action="/action_page.php"
    style="direction: rtl; margin-top: 30px; margin-right: 40px"
  >
    <label for="cars" style="margin-left: 10px">موضوع :</label>
    <select name="cars" id="cars" v-model="type">
      <option value="اضافه ظرفیت">{{ ezafe }}</option>
      <option value="تغییر ساعت امتحان">{{ timeChange }}</option>

      <option value="opel">گرفتن در از گرایش دیگر</option>
    </select>
    <br /><br />
    <label style="margin-left: 10px">نام درس :</label>
    <input type="text" v-model="courseName" />
    <br />

    <button
      type="submit"
      value="Submit"
      style="margin-top: 30px; margin-right: 40px"
      @click="sendReqData"
    >
      ثبت درخواست
    </button>
  </form>
</template>

<script>
export default {
  emits: ["add-request"],
  data() {
    return {
      ezafe: "اضافه ظرفیت",
      timeChange: "تغییر ساعت امتحان",
      courseName: "",
      type: "",
    };
  },
  methods: {
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
};
</script>
