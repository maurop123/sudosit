<template>
  <v-container fluid>
    <v-layout row wrap>
      <v-flex xs12 sm8 offset-sm2 md6 offset-md3 lg4 offset-lg4 xl2 offset-xl5>
        <div class="text-xs-center">
          <div class="headline">A Life Examined</div>
        </div>
        <div v-for="item in posts" :key="item.id">
          <v-card class="my-4">
            <v-card-media v-if="item.img"
              class="white--text"
              height="300px"
              :src="item.img"
            />
            <v-card-title v-if="item.title">
              <h2>{{ item.title }}</h2>
            </v-card-title>
            <v-card-text v-if="item.content">
              <div v-html="item.content"></div>
            </v-card-text>
            <v-card-actions v-if="item.link">
              <v-btn flat block class="blue--text"
                :to="`blog/${item.link}`"
              >
                Read More
              </v-btn>
            </v-card-actions>
          </v-card>
        </div>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
  export default {
    name: 'home-view',
    computed: {
      posts() {
        return this.$store.state.posts
      },
    },
    mounted() {
      this.$store.dispatch('getPosts')
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
