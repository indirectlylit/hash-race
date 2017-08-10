<template>

  <div>
    <h1>the fantastic hash race</h1>
    <h2>or, not exactly the best use of valuable time two days before going on vacation...</h2>
    <p>are you ready to race?</p>
    <p>
      <button v-if="yes" @click="yes = false" class="pure-button pure-button-primary">
        yes
      </button>
      <span v-else>
        all right! on your mark, get set...
        <button @click="$emit('begin')" class="pure-button pure-button-primary">GO!</button>
      </span>
      <button v-if="no && yes" @click="no = false" class="pure-button">
        no
      </button>
      <span v-if="!no && yes">
        wrong!
      </span>
    </p>
  </div>

</template>


<script>

  export default {
    name: 'output',
    data () {
      return {
        yes: true,
        no: true
      }
    }
  }

</script>


<style scoped>

  h2 {
    color: white;
  }

</style>
