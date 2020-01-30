<template>
  <div class="single-post-page">
    <section class="post">
      <h1 class="post-title">{{ loadedPost.title }}</h1>

      <p class="post-content">{{ loadedPost.p1 }}</p>
      <p class="post-content">{{ loadedPost.p2 }}</p>
      <p class="post-content">{{ loadedPost.p3 }}</p>
      <p class="post-content">{{ loadedPost.p4 }}</p>
      <p class="post-content">{{ loadedPost.p5 }}</p>
      <p class="post-content">{{ loadedPost.p6 }}</p>
      <p class="post-content">{{ loadedPost.p7 }}</p>
      <p class="post-content">{{ loadedPost.p8 }}</p>
      <p class="post-content">{{ loadedPost.p9 }}</p>
      <p class="post-content">{{ loadedPost.p10 }}</p>

    </section>
    <div class="post-details">
      <div class="post-detail">Last updated on {{ loadedPost.updatedDate | date}}</div>
      <div class="post-detail">Written by {{ loadedPost.author }}</div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  asyncData(context) {
    return axios
      .get(
        "https://biskits-db.firebaseio.com/posts/" + context.params.id + ".json"
      )
      .then(res => {
        return {
          loadedPost: res.data
        };
      })
      .catch(e => console.log(e));
  }
};
</script>


<style scoped>


.post {
  text-align: center;
  /* width: 70%; */
  /* margin: 0 auto; */
  background-color: rgb(236, 236, 236);
  color: rgb(47, 47, 47);
  font-size: 1.4rem;
  line-height: 2rem;
}

.post p{
  font-size:1vw;
}

@media (max-width: 768px) {
  .post {
    width: 90%;
    margin: auto;
  }
  .post p{
  font-size:4vw;
}
}

.post-title {
  margin: 0;
}

.post-details {
  padding: 10px;
  box-sizing: border-box;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

@media (min-width: 768px) {
  .post-details {
    flex-direction: row;
  }
}

.post-detail {
  color: rgb(88, 88, 88);
  margin: 0 10px;
}



.post-content {
  width: 80%;
  text-align: right;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 2rem;
  margin-top: 2rem;
}
</style>
