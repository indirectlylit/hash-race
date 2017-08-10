<template>

  <div>
    <div class="pure-g">
      <OutputHash
        hash="test"
        class="pure-u-1 pure-u-sm-2-3"
        :difficulty="0"
      />
      <InputHash hash="test" class="pure-u-1 pure-u-sm-1-3" />
    </div>
    <div>Time remaining: {{ secondsRemaining }}s</div>
  </div>

</template>


<script>

  import InputHash from './InputHash.vue';
  import OutputHash from './OutputHash.vue';

  export default {
    name: 'output',
    components: { InputHash, OutputHash },
    props: {},
    data () {
      return {
        secondsRemaining: 5,
      };
    },
    mounted() {
      console.log('starting...');
      setInterval(() => {
        this.secondsRemaining -= 1;
        if (!this.secondsRemaining) {
          this.$emit('done');
        }
      }, 1000)
    }
  }

</script>


<style scoped></style>
