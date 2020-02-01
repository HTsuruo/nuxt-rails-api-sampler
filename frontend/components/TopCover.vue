<template>
  <div class="cover-container">
    <div class="container">
      <h1>{{ title }}</h1>
      <p>{{ description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  // props: [
  //   'title',
  //   'description'
  // ]
  props: {
    title: String,
    description: String
  }
}
</script>

<style lang="scss" scoped>
  .cover-container {
    display: flex;
    align-items: center;
    height: 240px;
    background-color: #000;
    color: #fff;
    vertical-align: middle;
    h1 {
      font-weight: 800;
      font-size: 4rem;
    }
  }
</style>
