<template>

  <div>
    <form @submit="NEXT" class="pure-form pure-form-stacked">
      <fieldset>
        <legend>What is it?</legend>
        <input type="text" placeholder="hash">
        <button type="submit" class="pure-button pure-button-primary">NEXT!</button>
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
        console.log('NEXT', this.input);
      },
    },
  }

</script>


<style scoped></style>
