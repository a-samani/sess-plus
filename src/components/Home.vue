<template>
  <div
    class="nnady"
    style="background-color: #44a1a0; margin: 0px; padding: 0px"
  >
    <div class="dropdown">
      <button class="dropbtn" id="request">منو</button>
      <div class="dropdown-content">
        <a
          href="#"
          :style="showReq ? { 'background-color': ' #44a1a0' } : {}"
          @click="toReq"
          >نمایش درخواست ها</a
        >
        <a
          href="#"
          :style="addReq ? { 'background-color': ' #44a1a0' } : {}"
          @click="toAdd"
          >ثبت درخواست جدید</a
        ><a
          href="#"
          :style="isPrivate ? { 'background-color': ' #44a1a0' } : {}"
          @click="toPrivate"
          >پیگیری درخواست های شخصی</a
        >
      </div>
    </div>
    <div class="info">
      <h5>{{ student.name }} {{ student.user }}</h5>
    </div>


    <button id="lOut" @click="$emit('log-out')">lOut</button>


    <div v-if="showReq" class="myDiv" style="direction: rtl">
      <ul class="myReqs" style="border: 0px">
        <li class="reqli" id="reqli1">نوع</li>
        <li class="reqli" id="reqli2">درس</li>
        <li class="reqli" id="reqli3">تاریخ</li>
        <li class="reqli" id="reqli4">تعداد درخواست</li>
      </ul>
      <div v-for="req in requests" :key="req.key">
        <requests :request="req" @upvote="upVote" @downvote="downVote" />
      </div>
    </div>


    <div v-if="addReq" class="myDiv" style="direction: rtl">
      <add-request @add-request="addRequest"></add-request>
    </div>


    <div v-if="isPrivate" class="myDiv" style="direction: rtl"></div>
  </div>
</template>

<script>
import requests from "./Requests.vue";
import addRequest from "./AddRequest.vue";
export default {
  data() {
    return {
      showReq: true,
      addReq: false,
      isPrivate: false,
    };
  },
  components: { requests, addRequest },
  props: ["student", "requests"],
  emits: ["upvote", "downvote", "addReq"],
  methods: {
    upVote(id) {
      this.$emit("upvote", id, this.student.user);
    },
    downVote(id) {
      this.$emit("downvote", id, this.student.user);
    },
    toAdd() {
      this.showReq = false;
      this.addReq = true;
      this.isPrivate = false;
    },
    toReq() {
      this.showReq = true;
      this.addReq = false;
      this.isPrivate = false;
    },
    toPrivate() {
      this.showReq = false;
      this.addReq = false;
      this.isPrivate = true;
    },
    // toggleAddReqpage() {

    // },
    addRequest(type,name) {
        
      this.$emit("addReq", type,name, this.student.user);
    },
  },
};
</script>

<style>
#reqli1 {
  position: absolute;
  right: 20px;
}
.nnady {
  background-color: #44a1a0;
  background-image: url("../assets/home-back.png");
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-size: cover;
  min-height: 100vh;
  min-width: 100vh;
  display: flex;
  font-weight: 400;
}

body {
  background-color: #44a1a0;
}

#request {
  right: 150px;
  top: 100px;
}
#add-request {
  right: 150px;
  top: 150px;
}
.reqbtn {
  width: 170px;
  position: absolute;
  box-sizing: border-box;
  z-index: 4;
  height: 35px;

  padding: 0px;
  cursor: inherit;
  background: rgb(58, 77, 143) none repeat scroll 0% 0%;
  border: medium none;
  text-align: center;
  font-family: "Barlow";
  font-size: 16px;
  font-weight: 600;
  color: rgb(255, 255, 255);
  letter-spacing: 2px;
  line-height: 1;
  border-radius: 5px;
  transition: background 200ms ease 0s;
  box-shadow: none;
}

.myDiv {
  width: 1300px;
  left: 50px;
  position: absolute;
  box-sizing: border-box;
  z-index: 3;
  height: 484px;
  top: 100px;
  background-color: rgb(222, 222, 222);
  border-radius: 0px;
}
.info {
  direction: rtl;

  right: 150px;
  position: absolute;
  box-sizing: border-box;
  z-index: 3;
  height: 50px;
  top: 20px;

  border-radius: 0px;
}
#lOut {
  left: 50px;
  top: 20px;
  width: 50px;
  height: 50px;
  position: absolute;
}
.dropbtn {
  background-color: #4caf50;
  color: white;
  padding: 16px;
  font-size: 16px;
  border: none;
  cursor: pointer;
  width: 200px;
}

.dropdown {
  position: absolute;
  display: inline-block;
  top: 100px;
  right: -1450px;
}

.dropdown-content {
  display: none;
  position: absolute;
  right: 0;
  background-color: #f9f9f9;
  min-width: 200px;
  box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
  z-index: 1;
  direction: rtl;
}

.dropdown-content a {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
}

.dropdown-content a:hover {
  background-color: #f1f1f1;
}

.dropdown:hover .dropdown-content {
  display: block;
}

.dropdown:hover .dropbtn {
  background-color: #3e8e41;
}
li {
  direction: rtl;
  display: inline-block;
  margin: 0 10px;
}
</style>
