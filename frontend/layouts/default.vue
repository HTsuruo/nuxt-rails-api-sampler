<template>
  <div>
    <!-- <l-header /> -->
    <nuxt />
  </div>
</template>

<script>
// import LHeader from '~/layouts/header.vue'

export default {
  components: {
    // LHeader
  }
}
</script>

<style>
html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}

.container {
  /* bulmaの基本設定は残しつつ足りないレイアウト要素を追加 */
  margin: 80px auto;
}

</style>
