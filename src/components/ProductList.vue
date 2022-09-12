<template>
    <div class="product">
      <img
      :src="'https://image.tmdb.org/t/p/w342' + product.poster_path"
      :alt="product.original_title"
      class="poster"
      v-if="product.poster_path != null"
    />
    <img
      src="../assets/img/poster-notfound.png"
      alt=""
      class="poster"
      v-else
    />
      <div class="info">
        <ul>
          <li><strong>Titolo:</strong> {{ product.title }} {{ product.name }}</li>
          <li>
            <strong>Titolo originale:</strong> {{ product.original_title }}
            {{ product.original_name }}
          </li>
          <li>
            <strong>Lingua:</strong>
          </li>
          <li>
          <img
            :src="
              require(`../assets/img/flags/${product.original_language}.svg`)
            "
            :alt="product.original_language"
            class="lang"
          />
        </li>
          <li>
            <strong>Voto:</strong> <i
            v-for="(element, index) in getRating()"
            :key="index"
            class="fas fa-star rating-star"
          ></i>
          </li>
        </ul>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "ProductList",
    props: {
      product: Object,
    },
    methods: {
    getRating() {
      return Math.round(this.product.vote_average / 2);
    },
  },
  };
  </script>

<style lang="scss" scoped>
     @import "../assets/style/global.scss";
     .product {
  position: relative;
  width: 250px;
  height: 350px;
  background: #000;
  cursor: pointer;

  .poster {
    width: 250px;
    height: 350px;
    object-fit: cover;
  }

  .info {
    position: absolute;
    top: 0;
    width: 250px;
    height: 350px;
    opacity: 0;
    padding: 5px 15px;
    background: #000;
    transition: opacity 0.3s;

    &:hover {
      opacity: 1;
    }

    ul {
      list-style: none;

      li {
        margin: 10px 0;

        .lang {
          width: 32px;
        }

        .rating-star {
          color: #ffd700;
        }
      }
    }
  }
}
    </style>
    