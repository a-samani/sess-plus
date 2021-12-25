<template>
  <form style="line-height: 30px" @submit.prevent="Submit">
    <p style="direction: rtl; margin-top: 50px; font-size: 20px">
      معاونت محترم آموزشی دانشکده مهندسی برق و کامپیوتر
    </p>

    <p style="direction: rtl; font-size: 20px">با سلام و احترام</p>
    <p style="direction: rtl; font-size: 20px">
      درخواست می شود به دانشجوی آقا/خانم<label style="font-weight: bold">{{
        student.name
      }}</label>
      به شماره دانشجویی
      <label style="font-weight: bold">{{ student.user }}</label
      ><br />برای ترم جاری اجازه داده شود درس مذکور را از رشته های دیگر انتخاب
      واحد و اخذ نمایند.
    </p>
    <br />
    <div style="display: inline-block; margin-right: 10px">
      <label for="course name" style="margin-top: 10px">نام درس : </label>
      <input type="text" style="margin-right: 10px" v-model="courseName" />
    </div>

    <div style="display: inline-block; margin-right: 10px">
      <label for="course name" style="margin-top: 10px">شماره درس : </label>
      <input type="text" style="margin-right: 10px" v-model="courseNumber" />
    </div>

    <div style="display: inline-block; margin-right: 10px">
      <label for="course name" style="margin-top: 10px"
        >بخش ارائه دهنده درس :
      </label>
      <input type="text" style="margin-right: 10px" v-model="departmentName" />
    </div>

    <div style="display: inline-block; margin-right: 10px">
      <label for="course name" style="margin-top: 10px">گروه : </label>
      <input type="text" style="margin-right: 10px" v-model="group" />
    </div>

    <div style="display: inline-block; margin-right: 10px">
      <label for="course name" style="margin-top: 10px"> واحد : </label>
      <input type="text" style="margin-right: 10px" v-model="vahed" />
    </div>

    <div style="display: inline-block; margin-right: 10px">
      <label for="course name" style="margin-top: 10px">توضیحات : </label>
      <input type="text" style="margin-right: 10px" v-model="moreInfo" />
    </div>
    <br />
    <br />
    <div style="display: flex; justify-content: center; align-items: center">
      <button type="submit" style="left: 10%; top: 85%">ثبت درخواست</button>
    </div>
  </form>
</template>

<script>
export default {
  props: ["student", "type", "studentReqs"],
  data() {
    return {
      courseName: "",
      courseNumber: "",
      departmentName: "",
      group: "",
      vahed: "",
      moreInfo: "",
    };
  },
};
</script>

<style></style>
