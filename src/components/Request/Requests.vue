<template>
  <ul class="myReqs">
    <li class="reqli" id="reqli1">{{ request.type }}</li>
    <li class="reqli" id="reqli2">{{ request.courseName }}</li>
    <li class="reqli" id="reqli3">{{ request.date }}</li>
    <li class="reqli" id="reqli4">
      {{ request.applicant.length }}
    </li>
    <li class="reqli" id="reqli5"><button @click="upVote">درخواست دادن</button></li>
    <li class="reqli" id="reqli6"><button @click="downVote">برداشتن درخواست</button></li>
  </ul>
 
</template>

<script>
export default {
  props: ["request"],
  emits: ["upvote", "downvote"],
 
  data() {
    return {
      radif: Number(1),
    };
  },
  methods: {
    
    upVote() {
      this.$emit("upvote", this.request.key);
    },
    downVote() {
      this.$emit("downvote", this.request.key);
    },
    Alert() {
      alert(this.request.applicant.length);
    },
  },
};
</script>

<style>
.myReqs {
  direction: rtl;
  border: solid 2px blue;
  margin: 15px;

  font-size: 20px;
  height: 80px;
}
.reqli {
  margin-top: 15px;
}
#reqli1 {
  position: absolute;
  right: 20px;
}
#reqli2 {
  position: absolute;
  right: 200px;
}
#reqli3 {
  position: absolute;
  right: 400px;
}
#reqli4 {
  position: absolute;
  right: 700px;
}
#reqli5 {
  position: absolute;
  right: 900px;
}
#reqli6 {
  position: absolute;
  right: 1100px;
}
</style>
