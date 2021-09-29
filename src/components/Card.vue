<template>
  <div>
    <ul class="list-item">
      <li class="list-cards">
        <div class="img-cont">
          <img
            :src="'https://image.tmdb.org/t/p/w342' + info.poster_path"
            alt=""
          />
        </div>
        <div>
          <div class="card-info" v-if="info.title != null">
            Titolo: {{ info.title }}
          </div>
          <div class="card-info" v-else>Titolo: {{ info.name }}</div>
          <div class="card-info">
            Titolo Originale: {{ info.original_title }}
          </div>
          <div class="card-info">
            Lingua: <CountryFlag :country="flag(info.original_language)" />
          </div>
          <div class="card-info">Voto: {{ info.vote_average }}</div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import CountryFlag from "vue-country-flag";
export default {
  name: "Card",
  methods: {
    flag(info) {
      if (info == "en") {
        return "gb";
      } else if (info == "ja") {
        return "jp";
      } else if (info == "el") {
        return "gr";
      }
      return info;
    },
  },
  components: {
    CountryFlag,
  },
  props: ["movieList", "info"],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.list-item {
  background-color: white;
}
.card-info {
  min-height: 100px;
  padding-bottom: 10px;
}
img {
  min-width: 100%;
  min-height: 100%;
}
</style>
