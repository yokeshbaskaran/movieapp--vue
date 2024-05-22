<template>
  <div class="movie-detail">
    <div class="movie-item">
      <h2><span>Title:</span> {{ movie.Title }}</h2>
      <!-- <p>{{ $route.params.id }}</p> -->
      <span>{{ movie.Year }}</span>
      <div class="content">
        <img :src="movie.Poster" alt="Poster" class="featured-img" />
        <p>{{ movie.Plot }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, onBeforeMount } from "vue";
import { useRoute } from "vue-router";
import env from "@/env.js";

export default {
  name: "MovieDetail",
  setup() {
    const movie = ref({});
    const route = useRoute();

    onBeforeMount(() => {
      //fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&s=${search.value}`)

      fetch(
        `http://www.omdbapi.com/?apikey=${env.apikey}&i=${route.params.id}&plot=full`
      )
        .then((response) => response.json())
        .then((data) => {
          movie.value = data;
        });
    });

    return {
      movie,
      route,
    };
  },
};
</script>

<style lang="scss">
.movie-detail {
  width: 80%;
  margin: 2.5rem auto;
  padding: 10px;

  .movie-item {
    width: 90%;
    margin: 0 auto;

    h2 {
      color: #fff;
      font-size: 28px;
      font-weight: 600;
      margin-bottom: 16px;
    }

    span {
      color: #42b883;
    }
    .content {
      margin: 10px 0;
      display: flex;
      align-items: start;

      .featured-img {
        max-width: 180px;
        margin-inline: 0 16px;
      }

      p {
        color: #fff;
        font-size: 18px;
        line-height: 1.4;
        text-align: justify;
      }
    }
  }
}
</style>
