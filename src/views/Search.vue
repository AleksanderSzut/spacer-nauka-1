<template>
  <div class="wrapper">
    <div class="search">
      <label for="search">Search</label>
      <input name="search" id="search" v-model="searchValue" @input="handleInput">
      <ul>
        <li v-for="item in result" :key="item.data[0].nasa_id">
          <span>{{item.data[0].title}}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';

const API = 'https://images-api.nasa.gov/';


export default {
  name: 'Search',
  data() {
    return {
      searchValue: '',
      result: [],
    };
  },
  methods: {
    handleInput: debounce(function () {
      axios.get(`${API}/search?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.result = response.data.collection.items;
        })
        .catch((error) => {
          console.error(error);
        });
    }, 500),
  },
};
</script>

<style lang="scss" scoped>

  .wrapper
  {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin:0;
    padding: 30px;
    width: 100%;
  }

  .search
  {
    display: flex;
    flex-direction: column;
    width:250px;
    label
    {
      font-family: Montserrat, sans-serif;
    }
    input{
      height: 30px;
      border: 0;
      border-bottom: 1px solid black;
    }
  }

</style>
