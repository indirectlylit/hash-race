<template>

  <div class="pure-g">
    <OutputHash
      hash="test"
      class="pure-u-1 pure-u-sm-2-3"
      :difficulty="0"
    />
    <InputHash hash="test" class="pure-u-1 pure-u-sm-1-3" />
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
      return {};
    }
  }

</script>


<style scoped></style>
