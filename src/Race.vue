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
    <div class="time">Time remaining: {{ secondsRemaining }}s</div>
  </div>

</template>


<script>

  import InputHash from './InputHash.vue';
  import OutputHash from './OutputHash.vue';
  import hashes from './hashes.json';
  import shuffle from 'lodash.shuffle';

  const hashTypes = [ 'hex', 'pro', 'eng', 'swa' ];

  export default {
    name: 'output',
    components: { InputHash, OutputHash },
    props: {
      raceLength: {
        type: Number,
        required: true,
      }
    },
    data () {
      return {
        secondsRemaining: this.raceLength,
        hashIndex: 0,
        history: [],
      };
    },
    computed: {
      hashes() {
        return shuffle(hashes);
      },
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


<style scoped>

  .time {
    position: absolute;
    bottom: 0;
    left: 0;
    padding: 32px;
    color: gray;
  }

</style>
