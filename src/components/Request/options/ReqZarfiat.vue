<template>
  <form style="line-height: 30px" @submit.prevent="Submit">
    

    <p style="direction: rtl; font-size: 20px">
         <br />
     جهت اضافه ظرفیت درس :
      <input type="text" class="ZarfiatInput" v-model="courseName" />
    </p>
    <br />
    <p style="direction: rtl; font-size: 20px">
      استاد درس :
      <input type="text" class="ZarfiatInput" v-model="teacherName" />
    </p>
    <p style="direction: rtl; font-size: 20px">
      رئیس بخش : <input type="text" class="ZarfiatInput" v-model="director" />
    </p>
    <div style="display: flex; justify-content: center; align-items: center">
      <button type="submit" style="left: 10%; top: 85%">ثبت درخواست</button>
    </div>
  </form>
</template>

<script>
export default {
  props: ["type", "studentReqs"],
  inject: ['generalReqs'],
  data() {
    return {
      courseName: "",
      teacherName: "",
      director: "",
      listtt: [],
    };
  },
  methods: {
    Submit() {
      if (
        this.courseName === "" ||
        this.teacherName === "" ||
        this.director === ""
      ) {
        alert("please complete the form");
      } else {
        const newReqs = {
          id: "p" + new Date().toLocaleDateString("fa-IR"),
          type: this.type,
          isAccepted: null,
          counrse: this.courseName,
          teacher: this.teacherName,
          director: this.director,
          student: this.student,
        };
        console.log(typeof this.student.reqs);

        // this.studentReqs
        this.privateReqs.push(newReqs);
      }
    },
  },
};
</script>

<style>
.ZarfiatInput {
  height: 30px;
}
</style>


