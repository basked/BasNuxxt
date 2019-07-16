<template>
  <div class="bas-tool-bar">
    <bas-tool-bar></bas-tool-bar>
    <bas-nav-bar></bas-nav-bar>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
import BasToolBar from '~/components/BasToolBar.vue'
import '@fortawesome/fontawesome-free/css/all.min.css';
import '@fortawesome/fontawesome-free/js/all.min';
import BasNavBar from "../components/BasNavBar";

export default {
  components: {
    BasNavBar,
    Logo,
    BasToolBar
  }
}
</script>

<style>


</style>
