<template>

  <div>
    <h1>Nice!</h1>
    <p>
      <a :href="link">Submit this data</a>
    </p>
    <pre>
      {{ raw_data_json }}
    </pre>
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
    data () {
      return {};
    },
    computed: {
      raw_data_json() {
        return JSON.stringify(this.log);
      },
      link() {
        return `https://docs.google.com/forms/d/e/1FAIpQLSdnC_lnNW1FFh7JgP1EDUqUHQb5WDH8ZSCI_ebS4hOlHZSvag/viewform?usp=pp_url&entry.1382379487&entry.228374467=${this.overall_speed}&entry.602812913=${this.overall_error}&entry.710817806=${this.hex_speed}&entry.649177695=${this.hex_error}&entry.860806856=${this.humanhash_speed}&entry.487924097=${this.humanhash_error}&entry.7819285=${this.humanhashsw_speed}&entry.181999424=${this.humanhashsw_error}&entry.1049389761=${this.proquint_speed}&entry.1746002784=${this.proquint_error}&entry.1178689906=${this.raw_data_json}`;
      },
      overall_speed() {
        return 3
      },
      overall_error() {
        return 3
      },
      hex_speed() {
        return 3
      },
      hex_error() {
        return 3
      },
      humanhash_speed() {
        return 3
      },
      humanhash_error() {
        return 3
      },
      humanhashsw_speed() {
        return 3
      },
      humanhashsw_error() {
        return 3
      },
      proquint_speed() {
        return 3
      },
      proquint_error() {
        return 3
      },
    }
  }

</script>


<style scoped>

  pre {
    margin-top: 256px;
  }

</style>
