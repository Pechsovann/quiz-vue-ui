<template>
  <div class="timer">
    <h1>{{ time }}</h1>
    <md-spinner :md-progress="progress" class="md-warn"></md-spinner>
  </div>
</template>

<script>
    export default {
        name: "quiz-multi",
      props: ['time'],
      data() {
        return {
        };
      },
      computed: {
        progress() {
          return Math.round(3.33 * (30 - this.time));
        },
      },
    };
</script>

<style scoped>
  .timer {
    height: 100%;
    width: 100%;
    display: flex;
    flex-flow: column;
    justify-content: center;
    align-items: center;
  }
</style>
