<template>

  <div class="app">
    <Start v-if="state === 'start'" @begin="startRace" />
    <Race
      v-if="state === 'race'"
      @done="showResults"
      :raceLength="20"
    />
    <Finish v-if="state === 'finish'" :log="log" />
  </div>

</template>

<script>

  import Start from './Start.vue';
  import Race from './Race.vue';
  import Finish from './Finish.vue';

  export default {
    name: 'app',
    components: { Start, Race, Finish },
    methods: {
      startRace() {
        console.log('>>> START');
        this.state = 'race';
      },
      showResults(log) {
        console.log('>>> DONE', log);
        this.log = log;
        this.state = 'finish';
      },
    },
    data () {
      return {
        state: 'start',
        log: [],
      }
    }
  }

</script>

<style scoped>

  .app {
    margin: 32px;
  }

</style>
