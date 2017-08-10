<template>

  <div>
    <form @submit.prevent="NEXT" class="pure-form pure-form-stacked">
      <fieldset>
        <legend>What is it?</legend>
        <input v-model="input" type="text" placeholder="(the hash)" autofocus>
        <button type="submit" class="pure-button pure-button-primary" :disabled="input === ''">NEXT!</button>
      </fieldset>
    </form>
    <p class="note">
      case insensitive<br>
      spaces are optional<br>
      press NEXT or the 'enter' key<br>
    </p>
  </div>

</template>


<script>

  export default {
    name: 'input',
    data () {
      return {
        input: "",
      };
    },
    methods: {
      NEXT() {
        this.$emit('next', this.input);
        this.input = "";
      },
    },
  }

</script>


<style scoped>

  input {
    font-family: monospace;
  }

  .note {
    font-size: smaller;
    color: gray;
  }

</style>
