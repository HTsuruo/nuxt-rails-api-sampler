<template>
  <div>
    <top-cover title="Index." description="これはインデックスページです。リストが表示されます。" />
    <div class="container">
      <table class="table is-striped is-fullwidth">
        <thead>
          <th>ID</th>
          <th>タイトル</th>
          <th>説明</th>
          <th />
        </thead>
        <tbody>
          <tr>
            <td>aa</td>
            <td>名前</td>
            <td>など</td>
          </tr>
          <tr>
            <td>aa</td>
            <td>名前</td>
            <td>など</td>
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
  asyncData ({ $axios, params }) {
    return $axios.get('http://localhost:3000/posts')
      .then((res) => {
        console.log(res)
        return res
      })
  }
}
</script>
