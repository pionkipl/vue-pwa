<template>
  <div id="nav">
    <router-link to="/">Home</router-link>
  </div>
  <router-view/>
  <PWAPrompt />
</template>

<script>
import PWAPrompt from "@/components/PWAPrompt";
export default {
  name: 'App',
  components: {
    PWAPrompt
  }
}
</script>

<style lang="scss">
  @import "@/assets/sass/app";

  a {
    font-size: 5rem;
    color: #fff;
    text-decoration: none;
  }
</style>
