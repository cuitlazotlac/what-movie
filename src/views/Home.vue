<template>
  <div class="home">
    <div class="feature-card">
      <!-- <router-link to="/movie/tt0409591"> -->
      <!-- <img
          src="../assets/img/main_img.png"
          alt="Naruto Poster"
          class="featured-img"
        /> -->
      <!-- <div class="detail">
          <h3>Naruto</h3>
          <p>
            Naruto Uzumaki, a mischievous adolescent ninja, struggles as he
            searches for recognition and dreams of becoming the Hokage, the
            village's leader and strongest ninja.
          </p>
        </div> -->
      <!-- </router-link> -->
    </div>

    <form @submit.prevent="SearchMovies()" class="search-box">
      <input
        type="text"
        placeholder="&#xF002; What movie are you looking for?"
        style="font-family:Inter, FontAwesome"
        v-model="search"
      />
      <input type="submit" value="Search" />
    </form>

    <div class="movies-list">
      <div class="movie" v-for="movie in movies" :key="movie.imdbID">
        <router-link :to="'/movie/' + movie.imdbID" class="movie-link">
          <div class="product-image">
            <img :src="movie.Poster" alt="Movie Poster" />
            <div class="type">{{ movie.Type }}</div>
          </div>
          <div class="detail">
            <p class="year">{{ movie.Year }}</p>
            <h3>{{ movie.Title }}</h3>
          </div>
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
import env from "@/env.js";

export default {
  setup() {
    const search = ref("");
    const movies = ref([]);
    const SearchMovies = () => {
      if (search.value != "") {
        fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&s=${search.value}`)
          .then((response) => response.json())
          .then((data) => {
            movies.value = data.Search;
            search.value = "";
          });
      }
    };
    return {
      search,
      movies,
      SearchMovies,
    };
  },
};
</script>

<style lang="scss">
.home {
  .feature-card {
    position: relative;
    .featured-img {
      display: block;
      width: 100%;
      height: 450px;
      object-fit: cover;
      position: relative;
      z-index: 0;
    }
    .detail {
      position: absolute;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: rgba(0, 0, 0, 0.6);
      padding: 16px;
      z-index: 1;
      h3 {
        color: #fff;
        margin-bottom: 16px;
      }
      p {
        color: #fff;
      }
    }
  }
  .search-box {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 16px;
    input {
      display: block;
      appearance: none;
      border: none;
      outline: none;
      background: none;
      &[type="text"] {
        width: 100%;
        color: #181829;
        background-color: #ffffff;
        font-size: 20px;
        padding: 10px 16px;
        border-radius: 8px;
        margin-bottom: 15px;
        transition: 0.4s;
        &::placeholder {
          color: #2c2c2c38;
          font-size: 15px;
          font-weight: 900;
        }
        &:focus {
          box-shadow: 0px 3px 6px rgba(0, 0, 0, 0.2);
        }
      }
      &[type="submit"] {
        width: 100%;
        max-width: 300px;
        background-color: #f6c46a;
        padding: 16px;
        border-radius: 8px;
        color: #181829;
        font-size: 20px;
        font-weight: 600;
        text-transform: uppercase;
        transition: 0.4s;
        &:active {
          background-color: #181829;
          color: #f6c46a;
        }
      }
    }
  }
  .movies-list {
    display: flex;
    flex-wrap: wrap;
    margin: 0px 8px;
    .movie {
      max-width: 50%;
      flex: 1 1 25%;
      padding: 16px 8px;
      .movie-link {
        display: flex;
        flex-direction: column;
        height: 100%;
        .product-image {
          position: relative;
          display: block;
          img {
            display: block;
            width: 100%;
            border-radius: 8px 8px 0px 0px;
            // width: 28%;
            // height: 275px;
            object-fit: cover;
          }
          .type {
            position: absolute;
            padding: 8px 16px;
            // background-color: #F6C46A;
            background-color: #181829;
            border-radius: 0px 8px 8px 0px;
            color: #fff;
            bottom: 16px;
            left: 0px;
            text-transform: capitalize;
          }
        }
        .detail {
          background-color: #181829;
          padding: 16px 8px;
          height: 100px;
          flex: 1 1 100%;
          border-radius: 0px 0px 8px 8px;
          .year {
            color: #f6c46a;
            font-weight: 200;
            font-size: 14px;
          }
          h3 {
            color: #fff;
            font-weight: 600;
            font-size: 18px;
          }
        }
      }
    }
  }
}
</style>
