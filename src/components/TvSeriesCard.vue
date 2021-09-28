<template>
  <div>
    <ul class="list-item">
      <li class="list-cardss">
        <div class="card-info">Titolo: {{ infoTv.name }}</div>
        <div class="card-info">
          Titolo Originale: {{ infoTv.original_title }}
        </div>
        <div class="card-info">
          Lingua: <CountryFlag :country="infoTv.original_language" />
        </div>
        <div class="card-info">Voto: {{ infoTv.vote_average }}</div>
      </li>
    </ul>
  </div>
</template>

<script>
import CountryFlag from "vue-country-flag";
export default {
  name: "Card",
  components: {
    CountryFlag,
  },
  props: ["tvList", "infoTv"],
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
</style>
