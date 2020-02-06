<template>
  <div>
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
        <button @click="onClickUpdate" class="button is-link is-light is-fullwidth">
          編集する
        </button>
      </div>
      <div class="column">
        <button @click="deletePost" class="button is-danger is-light is-fullwidth">
          削除する
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  props: ['post', 'isEdit'],
  methods: {
    async deletePost () {
      await axios.delete(`http://localhost:3000/posts/${this.post.id}`)
      this.$router.push('/')
    },
    onClickUpdate () {
      this.isEdit = true
    }
  }
}
</script>
