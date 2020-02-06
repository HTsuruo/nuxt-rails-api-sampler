<template>
  <div>
    <top-cover title="Index." description="これはインデックスページです。リストが表示されます。" />
    <div class="container">
      <ul v-if="errors.length">
        <li v-for="error in errors" :key="error.index">
          <p>※{{ error }}</p>
        </li>
      </ul>
      <form id="createForm" @submit.prevent="onSubmit">
        <div class="columns">
          <div class="column">
            <input v-model="title" type="text" name="title" placeholder="タイトルを入力" class="input">
          </div>
          <div class="column">
            <input v-model="description" type="text" name="description" placeholder="説明文を入力" class="input">
          </div>
          <div class="column">
            <input type="submit" value="新規作成" class="button is-link is-light">
          </div>
        </div>
      </form>
      <table class="table is-striped is-fullwidth">
        <thead>
          <th>ID</th>
          <th>タイトル</th>
          <th>説明</th>
          <th />
        </thead>
        <tbody>
          <tr v-for="post in posts" :key="post.id">
            <td>{{ post.id }}</td>
            <td>{{ post.title }}</td>
            <td>{{ post.description }}</td>
            <td>
              <nuxt-link :to="`/posts/${post.id}`" class="button is-link is-light is-small">
                詳細へ
              </nuxt-link>
            </td>
          </tr>
        </tbody>
      </table>
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
  data () {
    return {
      title: '',
      description: '',
      errors: []
    }
  },
  async asyncData ({ $axios }) {
    const res = await $axios.get('http://localhost:3000/posts')
    // .catch((error) => {
    //   console.log(error)
    //   return false
    // })
    return { posts: res.data }
  },
  methods: {
    checkForm (e) {
      if (this.title && this.description) {
        return true
      }
      this.errors = []
      if (!this.title) {
        this.errors.push('タイトルを入力してください')
      }
      if (!this.description) {
        this.errors.push('説明文を入力してください')
      }
      return false
    },
    onSubmit (e) {
      if (this.checkForm(e)) {
        this.postData()
      }
    },
    async postData () {
      const data = {
        'title': this.title,
        'description': this.description
      }
      const res = await axios.post('http://localhost:3000/posts', data)
      this.posts.unshift(res.data)
      this.resetData()
    },
    resetData () {
      this.title = ''
      this.description = ''
    }
  }
}
</script>
