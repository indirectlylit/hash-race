<template>

  <div class="app">
    <Start v-if="state === 'start'" @begin="startRace" />
    <Race
      v-if="state === 'race'"
      @done="showResults"
      :raceLength="raceLength"
    />
    <Finish v-if="state === 'finish'" :log="log" />
  </div>

</template>

<script>

  import Start from './Start.vue';
  import Race from './Race.vue';
  import Finish from './Finish.vue';


  // https://stackoverflow.com/questions/901115/how-can-i-get-query-string-values-in-javascript
  function getParameter(name, url) {
    if (!url) url = window.location.href;
    name = name.replace(/[\[\]]/g, "\\$&");
    var regex = new RegExp("[?&]" + name + "(=([^&#]*)|&|#|$)"),
        results = regex.exec(url);
    if (!results) return null;
    if (!results[2]) return '';
    return decodeURIComponent(results[2].replace(/\+/g, " "));
  }

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
    data() {
      return {
        state: 'start',
        log: [],
        raceLength: 600,
      }
    },
    mounted() {
      const raceLength = getParameter('length', window.location.href);
      if (parseInt(raceLength)) {
        this.raceLength = parseInt(raceLength);
      }
    }
  }

</script>

<style scoped>

  .app {
    margin: 32px;
  }

</style>
