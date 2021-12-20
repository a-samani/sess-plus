<template>
  <form style="line-height: 30px" @submit.prevent="Submit">
    <p style="direction: rtl; margin-top: 50px; font-size: 20px">
      معاونت محترم آموزشی دانشکده مهندسی برق و کامپیوتر
    </p>

    <p style="direction: rtl; font-size: 20px">با سلام،</p>
    <p style="direction: rtl; font-size: 20px">
      احتراما آقا/خانم {{ student.name }} به شماره دانشجویی {{ student.user }}<br />جهت اضافه
      ظرفیت درس :
      <input type="text" class="ZarfiatInput" v-model="courseName" />معرفی می
      گردد.
    </p>
    <br />
    <p style="direction: rtl; font-size: 20px">
      استاد درس :
      <input type="text" class="ZarfiatInput" v-model="teacherName" />
    </p>
    <p style="direction: rtl; font-size: 20px">
      رئیس بخش : <input type="text" class="ZarfiatInput" v-model="director" />
    </p>
    <button type="submit" style="left: 50%; position: absolute">
      ثبت درخواست
    </button>
  </form>
</template>

<script>
export default {
  props: ['student','type'],

  data() {
    return {
      courseName: "",
      teacherName: "",
      director: "",
      
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
        console.log(this.student.name + this.user);
      } 
      else {
        // const newReqs = {
        //     id : new Date().toLocaleDateString("fa-IR"),
        //     type : this.type,
            
        // }
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
