<template>
  <footer class="footer">
    <div class="container-fluid">
      <nav class="pull-left">
        <ul>
          <li>
            <router-link :to="{path:'/admin'}">Dashboard</router-link>
          </li>
        </ul>
      </nav>
      <div class="copyright pull-right">
        &copy; Coded with
        <i class="fa fa-heart heart"></i> by
        <a href="https://github.com/ccfteam2/ccf6.0" target="_blank">Team 2</a>.
        Designed in <a href="http://www.cajuncodefest.org/" target="_blank">CajunCodefest</a>.
      </div>
    </div>
  </footer>
</template>
<script>
  export default {}

</script>
<style>

</style>
