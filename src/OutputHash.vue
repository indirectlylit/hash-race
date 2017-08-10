<template>

  <div class="content">
    {{ hash }}
  </div>

</template>


<script>

  export default {
    name: 'output',
    props: {
      hash: {
        type: String,
        required: true,
      },
    },
  }

</script>


<style scoped>

  .content {
    text-align: center;
  }

</style>
