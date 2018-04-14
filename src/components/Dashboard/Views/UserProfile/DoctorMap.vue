<template>

</template>
<!--<script src="https://cdn.plot.ly/plotly-latest.min.js"></script>-->
<script>

  export default {
    data () {
      return {
        state: 'LA'
      }
    },
    methods: {
      updateProfile () {
        alert('Your data: ' + JSON.stringify(this.user))
      }
    }
  }

</script>
<style>

</style>
