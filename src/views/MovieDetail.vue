<template>
  <div class="movie-detail">
    <h2>{{ movie.Title }}</h2>
    <p>{{ movie.Year }}</p>
    <br />
    <img :src="movie.Poster" alt="Movie Poster" class="featured-img" />
    <br />
    <p class="movie-desc">{{ movie.Plot }}</p>
  </div>
</template>

<script>
import { ref, onBeforeMount } from "vue";
import { useRoute } from "vue-router";
import env from "@/env.js";

export default {
  setup() {
    const movie = ref({});
    const route = useRoute();

    onBeforeMount(() => {
      fetch(
        `http://www.omdbapi.com/?apikey=${env.apikey}&i=${route.params.id}&plot=full`
      )
        .then((response) => response.json())
        .then((data) => {
          movie.value = data;
          console.log(data);
        });
    });

    return {
      movie,
    };
  },
};
</script>

<style lang="scss">
.movie-detail {
  padding: 16px;

  .featured-img {
    display: block;
    max-width: 250px;
    margin-bottom: 16px;
    margin: auto;
    border-radius: 8px;
  }

  h2 {
    color: #181829;
    font-size: 33px;
    font-weight: 900;
    margin-bottom: 16px;
    text-align: center;
  }

  p {
    color: #181829;
    font-size: 25px;
    font-weight: 500;
    line-height: 1.4;
    text-align: center;
  }

  .movie-desc {
    color: #181829;
    font-size: 20px;
    font-weight: 200;
    line-height: 1.4;
    text-align: justify;
    text-justify: inter-word;
    width: 80%;
    margin: auto;
  }
}
</style>
