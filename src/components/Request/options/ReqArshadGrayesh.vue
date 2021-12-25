<template>
  <form style="line-height: 30px" @submit.prevent="Submit">
    <h4 style="margin-top: 20px">
      مشخصات دانشجو :{{ student.name }} {{ student.user }}
    </h4>
    <div style="margin-top: 10px">
      <label
        for="grayesh"
        style="font-weight: bold; font-size: 20px; margin-left: 5px"
        >گرایش :
      </label>
      <input type="text" style="font-weight: bold" v-model="grayesh" />
    </div>
    <div style="margin-top: 10px">
      <label
        for="grayesh"
        style="font-weight: bold; font-size: 20px; margin-left: 5px"
        >استاد راهنما :
      </label>
      <input type="text" style="font-weight: bold" v-model="grayesh" />
    </div>
    <div style="margin-top: 10px">
      <label
        for="grayesh"
        style="font-weight: bold; font-size: 20px; margin-left: 5px"
        >تعداد واحد گذرانده :
      </label>
      <input type="text" style="font-weight: bold" v-model="grayesh" />
    </div>
    <hr />
    <h4>عنوان درخواست</h4>
    <div style="margin-top: 10px; display: inline-block">
      <label
        for="grayesh"
        style="font-weight: bold; font-size: 20px; margin-left: 5px"
        >متقاضی اخذ درس :
      </label>
      <input type="text" style="font-weight: bold" v-model="grayesh" />
    </div>
    <div style="margin-top: 10px; display: inline-block">
      <label
        for="grayesh"
        style="font-weight: bold; font-size: 20px; margin-left: 5px"
        >از گرایش :
      </label>
      <input type="text" style="font-weight: bold" v-model="grayesh" />
    </div>
    <br />
    <div style="margin-top: 10px; display: inline-block">
      <label
        for="grayesh"
        style="font-weight: bold; font-size: 20px; margin-left: 5px"
        >شماره درس :
      </label>
      <input type="text" style="font-weight: bold" v-model="grayesh" />
    </div>
    <div style="margin-top: 10px; display: inline-block">
      <label
        for="grayesh"
        style="font-weight: bold; font-size: 20px; margin-left: 5px"
        >گروه درس :
      </label>
      <input type="text" style="font-weight: bold" v-model="grayesh" />
    </div>
    <div style="margin-top: 10px">
      <label
        for="grayesh"
        style="font-weight: bold; font-size: 20px; margin-left: 5px"
        >استاد درس :
      </label>
      <input type="text" style="font-weight: bold" v-model="grayesh" />
    </div>
    <hr />
    <h4>برگذاری مدارک مورد نیاز</h4>
    <div>
      <form action="/action_page.php">
        <label
          style="font-weight: bold; font-size: 20px; margin-left: 5px"
          for="teacherSign"
          >بارگذاری امضا استاد درس</label
        >
        <input type="file" id="myFile" name="filename" />
        <br />
        <label
          style="font-weight: bold; font-size: 20px; margin-left: 5px"
          for="teacherSign"
          >بارگذاری امضا استاد راهنما</label
        >
        <input type="file" id="myFile" name="filename" />
        <br />
        <label
          style="font-weight: bold; font-size: 20px; margin-left: 5px"
          for="teacherSign"
          >بارگذاری امضا مدیر گروه(گرایش دانشجو)</label
        >
        <input type="file" id="myFile" name="filename" />
        <br />
        <label
          style="font-weight: bold; font-size: 20px; margin-left: 5px"
          for="teacherSign"
          >بارگذاری امضا مدیر گروه مقصد</label
        >
        <input type="file" id="myFile" name="filename" />
      </form>
    </div>
    <div style="display: flex; justify-content: center; align-items: center">
      <button type="submit" style="left: 10%; top: 85%">ثبت درخواست</button>
    </div>
  </form>
</template>

<script>
export default {
  props: ["student", "type", "studentReqs"],
  inject: ["privateReqs"],
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
