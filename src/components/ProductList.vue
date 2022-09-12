<template>
    <div class="product">
      
      <div class="info">
        <ul>
          <li><strong>Titolo:</strong> {{ product.title }} {{ product.name }}</li>
          <li>
            <strong>Titolo originale:</strong> {{ product.original_title }}
            {{ product.original_name }}
          </li>
          <li>
            <strong>Lingua:</strong> {{ product.original_language }}
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
            <strong>Voto:</strong> {{ product.vote_average }}
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
    
  };
  </script>

<style lang="scss" scoped>
     @import "../assets/style/global.scss";
    
    </style>
    