<template>
  <v-card class="mx-auto">
    <v-img :src="catchimg.url" height="300px" cover></v-img>
    <v-card-title> {{ title }} </v-card-title>

    <v-card-subtitle> {{ createAt }} </v-card-subtitle>
    <v-card-subtitle> {{ discription }} </v-card-subtitle>

    <v-card-text>
      {{ body }}
    </v-card-text>

    <v-card-actions>
      <v-spacer></v-spacer>
    </v-card-actions>
  </v-card>
</template>
<script>
import axios from 'axios'
export default {
  name: 'BlogItem',
  async asyncData({ params }) {
    const { data } = await axios.get(
      `https://llxi2ry41r.microcms.io/api/v1/blog/${params.id}`,
      {
        headers: {
          'X-MICROCMS-API-KEY': '585879871bc84a3fb0d272589711857d421e',
        },
      }
    )
    return data
  },
}
</script>
