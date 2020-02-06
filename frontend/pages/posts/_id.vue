<template>
  <div>
    <top-cover title="Detail." description="選択されたコンテンツの詳細が表示されます" />
    <div class="container">
      <div class="columns">
        <div class="column is-half">
          <post-edit :post="post" :isEdit="isEdit" v-if="isEdit" />
          <post-detail :post="post" :isEdit="isEdit" v-else />
          <nuxt-link to="/" class="button is-light is-fullwidth back-btn">
            一覧画面へ
          </nuxt-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TopCover from '~/components/TopCover.vue'
import PostDetail from '~/components/PostDetail.vue'
import PostEdit from '~/components/PostEdit.vue'

export default {
  components: {
    TopCover,
    PostDetail,
    PostEdit
  },
  data () {
    return {
      isEdit: false
    }
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

<style lang="scss" scoped>
.back-btn {
  margin-top: 24px;
}
</style>
