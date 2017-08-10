<template>

  <div class="app">
    <Start v-if="state === 'start'" />
    <Race v-if="state === 'race'" />
    <Finish v-if="state === 'finish'" />
  </div>

</template>

<script>

  import Start from './Start.vue';
  import Race from './Race.vue';
  import Finish from './Finish.vue';

  export default {
    name: 'app',
    components: { Start, Race, Finish },
    data () {
      return {
        state: 'race',
      }
    }
  }

</script>

<style scoped>

  .app {
    margin: 32px;
  }

</style>
