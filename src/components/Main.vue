<template>
  <main class="container w-75 my-5 mx-auto d-flex">
    <div class="row">
      <h1>film</h1>
      <div class="col-2" v-for="movie in movieList" :key="movie.id">
        <Card :info="movie" :movieList="movieList" :key="movie.id" />
      </div>
      <h1>TvSeries</h1>
      <div class="col-2" v-for="tv in tvList" :key="tv.id">
        <Card :info="tv" :movieList="tvList" :key="tv.id" />
      </div>
    </div>
  </main>
</template>

<script>
import Card from "./Card.vue";

export default {
  name: "Main",
  components: {
    Card,
  },
  props: ["movieList", "tvList"],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss"></style>
