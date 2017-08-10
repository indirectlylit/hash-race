<template>

  <div>
    <h1>Done!</h1>
    <p>You typed {{ log.length }} hash{{ log.length === 1 ? '. Sad.' : 'es' }}
    <p>
      <a :href="link" target="_blank">Submit this data</a> (opens in a new tab)
    </p>
    <table class="pure-table pure-table-horizontal" v-if="log.length">
      <thead>
        <tr>
          <th>Hash</th>
          <th class="num">Avg Speed</th>
          <th class="num">Error rate</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Overall</td>
          <td class="num">{{ (overall_speed).toFixed(2) }} s</td>
          <td class="num">{{ (overall_error).toFixed(1) }}%</td>
        </tr>
        <tr v-if="hex.length">
          <td>Hexadecimal</td>
          <td class="num">{{ (hex_speed).toFixed(2) }} s</td>
          <td class="num">{{ (hex_error).toFixed(1) }}%</td>
        </tr>
        <tr v-if="eng.length">
          <td>English</td>
          <td class="num">{{ (humanhash_speed).toFixed(2) }} s</td>
          <td class="num">{{ (humanhash_error).toFixed(1) }}%</td>
        </tr>
        <tr v-if="swa.length">
          <td>Swahili</td>
          <td class="num">{{ (humanhashsw_speed).toFixed(2) }} s</td>
          <td class="num">{{ (humanhashsw_error).toFixed(1) }}%</td>
        </tr>
        <tr v-if="pro.length">
          <td>Proquint</td>
          <td class="num">{{ (proquint_speed).toFixed(2) }} s</td>
          <td class="num">{{ (proquint_error).toFixed(1) }}%</td>
        </tr>
      </tbody>
    </table>
  </div>

</template>


<script>

  export default {
    name: 'finish',
    props: {
      log: {
        type: Array,
        required: true,
      }
    },
    methods: {
      filtered(type) {
        return this.log.filter(item => item.type === type);
      },
      avgSpeed(array) {
        if (!array.length) {
          return NaN;
        }
        return array.reduce((sum, item) => sum + item.time, 0) / array.length;
      },
      compare(a, b) {
        return a.replace(' ', '').toLowerCase() === b.replace(' ', '').toLowerCase();
      },
      errorRate(array) {
        const bad = array.reduce(
          (sum, item) => {
            return this.compare(item.input, item.output) ? sum : sum + 1;
          },
          0
        );
        return 100.0 * bad / array.length;
      },
    },
    computed: {
      link() {
        return `https://docs.google.com/forms/d/e/1FAIpQLSdnC_lnNW1FFh7JgP1EDUqUHQb5WDH8ZSCI_ebS4hOlHZSvag/viewform?usp=pp_url&entry.1382379487&entry.228374467=${this.overall_speed}&entry.602812913=${this.overall_error}&entry.710817806=${this.hex_speed}&entry.649177695=${this.hex_error}&entry.860806856=${this.humanhash_speed}&entry.487924097=${this.humanhash_error}&entry.7819285=${this.humanhashsw_speed}&entry.181999424=${this.humanhashsw_error}&entry.1049389761=${this.proquint_speed}&entry.1746002784=${this.proquint_error}&entry.1178689906=${this.raw_data_json}`;
      },

      hex() { return this.filtered('hex'); },
      eng() { return this.filtered('eng'); },
      swa() { return this.filtered('swa'); },
      pro() { return this.filtered('pro'); },

      overall_speed() { return this.avgSpeed(this.log); },
      hex_speed() { return this.avgSpeed(this.hex); },
      humanhash_speed() { return this.avgSpeed(this.eng); },
      humanhashsw_speed() { return this.avgSpeed(this.swa); },
      proquint_speed() { return this.avgSpeed(this.pro); },

      overall_error() { return this.errorRate(this.log) },
      hex_error() { return this.errorRate(this.hex) },
      humanhash_error() { return this.errorRate(this.eng) },
      humanhashsw_error() { return this.errorRate(this.swa) },
      proquint_error() { return this.errorRate(this.pro) },

      raw_data_json() { return JSON.stringify(this.log); },
    }
  }

</script>


<style scoped>

  .num {
    text-align: right;
  }

</style>
