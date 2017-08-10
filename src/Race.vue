<template>

  <div>
    <div class="pure-g">
      <OutputHash
        :hash="hashes[hashIndex].input"
        class="pure-u-1 pure-u-sm-2-3"
      />
      <InputHash @next="next" class="pure-u-1 pure-u-sm-1-3" />
    </div>
    <!--
    <div class="time">
      Time remaining: {{ secondsRemaining }}s
      <br>
      Previous entry: {{ prevTime }}s
    </div>
     -->
  </div>

</template>


<script>

  import InputHash from './InputHash.vue';
  import OutputHash from './OutputHash.vue';
  import hashes from './hashes.json';
  import shuffle from 'lodash.shuffle';

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
        hashStartTime: new Date(),
      };
    },
    computed: {
      hashes() {
        return shuffle(hashes);
      },
      prevTime() {
        if (!this.history.length) {
          return 0;
        }
        return this.history[this.history.length-1].time;
      },
    },
    methods: {
      next(value) {
        console.log('NEXT', value);
        const now = new Date();
        this.history.push({
          type: this.hashes[this.hashIndex].type,
          input: this.hashes[this.hashIndex].input,
          output: value,
          time: (now - this.hashStartTime) / 1000,
        });
        this.hashStartTime = now;
        this.hashIndex += 1;
      }
    },
    mounted() {
      console.log('starting...');
      setInterval(() => {
        this.secondsRemaining -= 1;
        if (!this.secondsRemaining) {
          this.$emit('done', this.history);
        }
      }, 1000)
    }
  }

</script>


<style scoped>

  .time {
    bottom: 0;
    left: 0;
    padding: 32px;
    color: gray;
    margin-top: 150px;
    text-align: center;
    font-size: small;
  }

</style>
