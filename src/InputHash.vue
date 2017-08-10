<template>

  <div>
    <form @submit.prevent="NEXT" class="pure-form pure-form-stacked">
      <fieldset>
        <legend>What is it?</legend>
        <input v-model="input" type="text" placeholder="(the hash)" autofocus>
        <button type="submit" class="pure-button pure-button-primary" :disabled="input === ''">NEXT!</button>
      </fieldset>
    </form>
  </div>

</template>


<script>

  export default {
    name: 'input',
    props: {
      hash: {
        type: String,
        required: true,
      },
    },
    data () {
      return {
        input: "",
      };
    },
    methods: {
      NEXT() {
        this.input = ""
      },
    },
  }

</script>


<style scoped>

  input {
    font-family: monospace;
  }

</style>
