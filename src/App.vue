<template>
  <div class="container">
    <header></header>
    <div class="row">
      <div class="col-md-12">
        <router-view></router-view>
      </div>
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue';
export default {
  components: {
    header: Header
  }
}
</script>

<style>

</style>
