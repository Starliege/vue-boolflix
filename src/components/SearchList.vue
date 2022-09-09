<template>
    <div class="search">
      <input
        type="text"
        v-model.trim="inputSearch"
        @keyup.enter="$emit('research', inputSearch)"
      />
      <input
        type="submit"
        value="Cerca"
        @click="$emit('research', inputSearch)"
      />
    </div>
  </template>
  
  <script>
  export default {
    name: "SearchList",
    data() {
      return {
        inputSearch: "",
      };
    },
  };
  </script>
  <style lang="scss" scoped>
    @import "../assets/style/global.scss";
    
    input {
      outline: none;
      border: none;
      font-size: 1.2rem;
      color: #000;
    }
    
    
    </style>