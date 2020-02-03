<template>
  <div>
    <top-cover title="Detail." description="選択されたコンテンツの詳細が表示されます" />
    <div class="container">
      <div class="columns">
        <div class="column is-half">
          <table class="table is-fullwidth">
              <tbody>
                <tr>
                  <td>ID</td>
                  <td>{{ post.id }}</td>
                </tr>
                <tr>
                  <td>タイトル</td>
                  <td>{{ post.title }}</td>
                </tr>
                <tr>
                  <td>説明</td>
                  <td>{{ post.description }}</td>
                </tr>
                <tr>
                  <td>作成日</td>
                  <td>{{ post.created_at }}</td>
                </tr>
              </tbody>
          </table>
          <nuxt-link to="/" class="button is-link is-light">一覧画面へ</nuxt-link>
        </div>
      </div>
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
