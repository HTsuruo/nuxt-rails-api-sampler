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
          <div class="columns">
            <div class="column">
              <button class="button is-link is-light is-fullwidth">
                編集する
              </button>
            </div>
            <div class="column">
              <button @click="deletePost" class="button is-danger is-light is-fullwidth">
                削除する
              </button>
            </div>
          </div>
          <nuxt-link to="/" class="button is-light is-fullwidth">
            一覧画面へ
          </nuxt-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import TopCover from '~/components/TopCover.vue'

export default {
  components: {
    TopCover
  },
  validate ({ params }) {
    // パスパラメータは数値以外NG
    this.uniqueid = params.id
    return /^\d+$/.test(this.uniqueid)
  },
  async asyncData ({ $axios, params }) {
    const res = await $axios.get(`http://localhost:3000/posts/${params.id}`)
    return { post: res.data }
  },
  methods: {
    async deletePost () {
      await axios.delete(`http://localhost:3000/posts/${this.post.id}`)
      this.$router.push('/')
    }
  }
}
</script>

<style lang="scss" scoped>

  .back-btn {
    display: block;
    margin-top: 60px;
  }

</style>
