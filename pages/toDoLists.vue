<template>
  <div>
      <v-container fluid>
        <v-row row wrap>
          <v-col v-for="item in contents" :key="item.id" xs12 sm6 md4>
            <Card :title="item.title" :content="item.detail"/>
          </v-col>
        </v-row>
      </v-container>
  </div>
</template>

<script>
import Card from '~/components/Card.vue'
export default {
  components: {
    Card
  },
  async asyncData({ app }) {
    const contents = await app.$axios.$get(process.env.API_BASE+'/api/to_dos')
    return { contents }
  },
}
</script>
