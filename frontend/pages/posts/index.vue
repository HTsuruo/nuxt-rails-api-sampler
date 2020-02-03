<template>
  <div>
    <top-cover title="Index." description="これはインデックスページです。リストが表示されます。" />
    <div class="container">
      <table class="table is-striped is-fullwidth">
        <thead>
          <th>ID</th>
          <th>タイトル</th>
          <th>説明</th>
        </thead>
        <tbody>
          <tr v-for="post in posts" :key="post.id">
            <td>
              <nuxt-link :to="`/posts/${post.id}`">
                {{ post.id }}
              </nuxt-link>
            </td>
            <td>{{ post.title }}</td>
            <td>{{ post.description }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import TopCover from '~/components/TopCover.vue'

export default {
  components: {
    TopCover
  },
  async asyncData ({ $axios }) {
    const res = await $axios.get('http://localhost:3000/posts')
    // .catch((error) => {
    //   console.log(error)
    //   return false
    // })
    return { posts: res.data }
  }
}
</script>
