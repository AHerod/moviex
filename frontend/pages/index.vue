<template>
  <v-row justify="center" align="center">
    <v-col class="d-flex">
      <v-card v-for="(movie, index) in movies" :key="index" class="pa-4 ma-4">
        <v-img
          height="250"
          :src="'http://localhost:1337' + movie.cover.url"
        ></v-img>
        <v-card-title class="headline">
          {{movie.Title}}
        </v-card-title>
        <v-card-text>
          <p>
            {{ movie.brief }}
          </p>
        </v-card-text>
        <v-card-actions>
          <v-spacer />
          <v-btn
            color="primary"
            nuxt
            to="/inspire"
          >
            Continue
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'
import moviesQuery from '~/apollo/queries/movie/movies'

export default {
  components: {
    Logo,
    VuetifyLogo
  },
  data() {
    return {
      // Initialize an empty restaurants variabkle
      movies: [],
      query: ''
    }
  },
  apollo: {
    movies: {
      prefetch: true,
      query: moviesQuery
    }
  },
}
</script>
