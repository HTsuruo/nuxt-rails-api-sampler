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
          <td><input v-model="title" type="text" class="input"></td>
        </tr>
        <tr>
          <td>説明</td>
          <td><input v-model="description" type="text" class="input"></td>
        </tr>
        <tr>
          <td>作成日</td>
          <td>{{ post.created_at }}</td>
        </tr>
      </tbody>
    </table>
    <div class="columns">
      <div class="column">
        <button class="button is-light is-fullwidth">
          キャンセル
        </button>
      </div>
      <div class="column">
        <button @click="updatePost" class="button is-primary is-light is-fullwidth">
          更新する
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  props: ['post'],
  data () {
    return {
      title: this.post.title,
      description: this.post.description
    }
  },
  methods: {
    async updatePost () {
      const data = {
        'title': this.title,
        'description': this.description
      }
      await axios.patch(`http://localhost:3000/posts/${this.post.id}`, data)
      // this.$router.push(`/posts/${this.post.id}`)
    }
  }
}
</script>
