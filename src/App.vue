<template>
  <div>
    <Header @searchText="getInput" />
    <Main :movieList="movieList" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      inputText: "",
      ApiUrl:
        "https://api.themoviedb.org/3/search/movie?api_key=872ce842efdff13fb216c98c572ff2fd",
      movieList: [],
    };
  },
  created() {
    this.getList();
  },
  computed: {
    filteredMovieList() {
      if (this.myQuery === "") {
        return this.movieList;
      }
      let filteredList = this.getList();
      return filteredList;
    },
  },
  methods: {
    getInput(text) {
      this.inputText = text;
      console.log(this.inputText);
      this.getList();
    },
    getList() {
      axios
        .get(this.ApiUrl + (this.inputText ? "&query=" + this.inputText : ""))
        .then((res) => {
          console.log(res.data.results);
          this.movieList = res.data.results;
        });
    },
  },
};
</script>

<style lang="scss">
@import "./style/general.scss";
</style>
