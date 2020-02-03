<template>
  <div>
    <top-cover title="Detail." description="選択されたコンテンツの詳細が表示されます" />
    <div class="container">
      ああ
      {{ post }}
    </div>
  </div>
</template>

<script>
import TopCover from '~/components/TopCover.vue'

export default {
  components: {
    TopCover
  },
  validate ({ params }) {
    // パスパラメータは数値以外NG
    return /^\d+$/.test(params.id)
  },
  async asyncData ({ $axios, params }) {
    const res = await $axios.get(`http://localhost:3000/posts/${params.id}`)
    return { post: res.data }
  }
}
</script>
