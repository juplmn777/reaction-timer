<template>
  <div @click="stopTimer" class="block" v-if="showBlock">click me</div>
</template>

<script>
export default {
  props: ['delay'],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit('end', this.reactionTime);
    },
  },
};
</script>

<style scoped>
.block {
  width: 400px;
  border-radius: 10px;
  background: #ff4b5c;
  color: #f1f1f1;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 100px 0;
  font-size: 25px;
  margin: 50px auto;
}
</style>
