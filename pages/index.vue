<template>
  <div class="container">
    <div>
      <logo />
      <h1 class="title">
        jeidiidx Lab.
      </h1>
      <navi />
    </div>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
import Navi from '~/components/Navi.vue'

export default {
  components: {
    Logo,
    Navi
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  background-color: #f9fcff;
}

.title {
  font-family: 'Noto Sans', 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 2px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
