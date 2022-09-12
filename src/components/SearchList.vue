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
input[type="text"] {
  padding: 3px 5px;
  background: #fff;
  width: 300px;
  border-radius: 5px 0 0 5px;
}
input[type="submit"] {
  padding: 3px 10px;
  background: #e6e6e6;
  border-radius: 0 5px 5px 0;
  cursor: pointer;

  &:hover {
    background: #d8d8d8;
  }
}
    
    
    </style>