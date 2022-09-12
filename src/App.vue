<template>
  <div id="app">
    <header>
      <a href="#" class="logo"
        ><img src="./assets/img/boolflix.png" alt="Boolflix"
      /></a>
      <SearchList @research="getResearch" />
    </header>
    <main>
      <div class="title">Movies</div>
      <div class="container">
        <ProductList
          v-for="(element, index) in moviesArr"
          :key="index"
          :product="element"
        />
      </div>

      <div class="title">Series</div>
      <div class="container">
        <ProductList
          v-for="(element, index) in seriesArr"
          :key="index"
          :product="element"
        />
      </div>
    </main>
  </div>
</template>

<script>
import axios from "axios";
import SearchList from "./components/SearchList.vue";
import ProductList from "./components/ProductList.vue";

export default {
    name: "App",
    data() {
        return {
            apiURLmovies: "https://api.themoviedb.org/3/search/movie",
            apiURLseries: "https://api.themoviedb.org/3/search/tv",
            moviesArr: [],
            seriesArr: [],
            searchQuery: "",
        };
    },
    methods: {
        getMovies() {
            axios
                .get(this.apiURLmovies, {
                params: {
                    api_key: "09e726836588fda16d1e69b5fd89e7d7",
                    query: this.searchQuery,
                },
            })
                .then((response) => {
                this.moviesArr = response.data.results;
                console.log(this.moviesArr);
            })
                .catch(function (error) {
                console.log(error);
            });
        },
        getSeries() {
            axios
                .get(this.apiURLseries, {
                params: {
                    api_key: "09e726836588fda16d1e69b5fd89e7d7",
                    query: this.searchQuery,
                },
            })
                .then((response) => {
                this.seriesArr = response.data.results;
                console.log(this.seriesArr);
            })
                .catch(function (error) {
                console.log(error);
            });
        },
        getResearch(inputSearch) {
            this.searchQuery = inputSearch;
            this.getMovies();
            this.getSeries();
        },
    },
    components: { SearchList, ProductList }
};
</script>

<style lang="scss">
@import "./assets/style/global.scss";

header {
  display: flex;
  align-items: center;
  padding: 25px 15px;
  background: #000;
  justify-content: space-around;

  & > .logo {
    font-size: 2rem;
    height: 40px;
  }
    img {
      height: 40px;
    }

  
}

main {
  padding: 50px 100px;
  min-height: calc(100vh);
  background: #191919;

  .title {
    margin: 0 100px 50px 50px;
    font-size: 3rem;
  }

  .container {
    display: flex;
    flex-wrap: wrap;
    gap: 30px;
    margin: auto auto 100px auto;
    width: 85%;
  }
}
</style>
