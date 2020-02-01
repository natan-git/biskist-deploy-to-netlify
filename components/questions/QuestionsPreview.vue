<template>
  <div class="question-content">
    <p>{{ question }}</p>
    <transition name="slide-fade">
        <p v-if="isShow">{{ answer }}</p>
    </transition>
    <img
      v-if="isArrow"
      class="read-more-icon"
      @click="showAnswer"
      src="@/assets/img/read-more-icon.svg"
      alt
    />
    <img
      v-if="!isArrow"
      class="read-more-icon"
      @click="showAnswer"
      src="@/assets/img/arrow-up.svg"
      alt
    />
  </div>
</template>

<script>
export default {
  name: "QuestionsPreview",
  props: {
    id: {
      type: String,
      required: true
    },
    isAdmin: {
      type: Boolean,
      required: true
    },
    question: {
      type: String,
      required: true
    },
    answer: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      isShow: false,
      isArrow: true
    };
  },
  computed: {},
  methods: {
    showAnswer() {
      this.isShow = !this.isShow;
      this.isArrow = !this.isArrow;
    }
  }
};
</script>


<style scoped>
.question-content {
  padding: 1rem;
  border-bottom: 2px rgb(39, 172, 238) solid;
}

.read-more-icon {
  float: left;
  width: 1rem;
  height: 1rem;
}

.slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-leave-active {
  transition: all .3s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to{
  transform: translateY(-10px);
  opacity: 0;
}

</style>
