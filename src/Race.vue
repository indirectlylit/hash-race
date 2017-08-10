<template>

  <div>
    <OutputHash hash="test" />
    <InputHash hash="test" />
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
