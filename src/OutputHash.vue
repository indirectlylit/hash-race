<template>

  <div class="wrapper">
    <div
      class="hash animated infinite"
      :class="animClass"
      :style="animDuration">{{ hash }}</div>
  </div>

</template>


<script>



  export default {
    name: 'output',
    props: {
      difficulty: {
        type: Number, // [0, 1]
      },
      hash: {
        type: String,
        required: true,
      },
    },
    computed: {
      animClass() {
        return 'wobble';
        // if (this.difficulty > 0.9) {
        //   return 'zoomOutRight';
        // }
        // if (this.difficulty > 0.75) {
        //   return 'wobble';
        // }
        // if (this.difficulty > 0.5) {
        //   return 'rubberBand';
        // }
        // if (this.difficulty > 0.25) {
        //   return 'swing';
        // }
      },
      animDuration() {
        const duration = 5+'s';
        // const duration = 50*(1.01 - this.difficulty) + 's';
        return { 'animation-duration': duration };
      },
    },
  }

</script>


<style scoped>

  .wrapper {
    text-align: center;
    height: 300px;
    width: 300px;
    margin: auto;
  }

  .hash {
    position: relative;
    top: 150px;
    font-size: large;
    font-family: monospace;
    user-select: none;
  }

</style>
