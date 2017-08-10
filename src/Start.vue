<template>

  <div>
    <h1>the fantastic hash race</h1>
    <p>are you ready to race?</p>
    <p>
      <button v-if="yes" @click="yes = false">
        yes
      </button>
      <span v-else>
        all right! On your mark, get set,
        <button @click="$emit('begin')">GO!</button>
      </span>
      <button v-if="no && yes" @click="no = false">
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


<style scoped></style>
