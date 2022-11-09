<template>
  <div>
    <div>MicroCMS</div>
    <v-row>
      <v-col v-for="blogItem in contents" :key="blogItem.id" cols="12" sm="6">
        <v-card class="mx-auto" max-width="344">
          <v-img :src="blogItem.catchimg.url" height="200px" cover></v-img>
          <v-card-title> {{ blogItem.title }} </v-card-title>

          <v-card-subtitle> {{ blogItem.createAt }} </v-card-subtitle>

          <v-card-text>
            {{ blogItem.discription }}
          </v-card-text>

          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn :to="`/blog/${blogItem.id}`">記事詳細</v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'IndexPage',
  async asyncData() {
    const { data } = await axios.get(
      // your-service-id部分は自分のサービスidに置き換えてください
      'https://llxi2ry41r.microcms.io/api/v1/blog',
      {
        // your-api-key部分は自分のapi-keyに置き換えてください
        headers: {
          'X-MICROCMS-API-KEY': '585879871bc84a3fb0d272589711857d421e',
        },
      }
    )
    return data
  },
}
</script>
