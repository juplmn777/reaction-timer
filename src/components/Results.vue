<template>
  <div class="scoreboard">
    <p class="result">
      Your reaction time : <span>{{ score }}</span> ms
    </p>
    <p class="rank-comment">
      {{ rank }}
    </p>
  </div>
</template>

<script>
export default {
  props: ['score'],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 300) {
      this.rank = 'Faster than Flash !!!';
    } else if (this.score < 400) {
      this.rank = 'Rapid reflexes !';
    } else {
      this.rank = '🐌🐌🐌 Snail pace...';
    }
  },
};
</script>

<style scoped>
.scoreboard {
  margin: 50px auto;
  padding: 20px;
  background: #1A1A2E;
  color: #f1f1f1;
  max-width: 25%;
  border-radius: 5px;
  box-shadow: 5px 5px 5px #000;
}

.result {
  font-size: 25px;
}

span {
  font-weight: bold;
  color: #ff4b5c;
}

.rank-comment {
  font-size: 30px;
  font-weight: bold;
  color: #ff4b5c;
}
</style>
