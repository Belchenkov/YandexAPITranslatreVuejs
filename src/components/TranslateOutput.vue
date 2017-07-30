<template>
    <h2 id="output" class="text-success well col-md-4 col-md-offset-4" >{{traslatedText}}</h2>
</template>

<script>
  export default {
    name: 'translateOutput',
    props: ['traslatedText']
  }
</script>

<style>
    h2#output {
        font-size: 32px;
        font-weight: bold;
        text-shadow: 0 1px 2px #000;
    }
</style>
