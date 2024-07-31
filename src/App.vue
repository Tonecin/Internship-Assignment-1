<template>
  <span>
    <button @click="addFilm" :disabled="index >= films.length">Add Film</button>
  </span>
  <span>Liked: {{ likeCount }}</span>
  <span>Dislike: {{ dislikeCount }}</span>
  <p></p>
  <div>
    <Film 
    v-for="item in films.slice(0, index)" 
    :film = "item" 
    @like-change="updateLike"
    @dislike-change="updateDislike"/>
  </div>
</template>

<script>
import Film from './components/Film.vue'
import jsonData from './assets/filmdata.json'

const filmData = jsonData.films

export default {
  data() {
    return {
      films: filmData,
      index: 3,
      likeCount: 0,
      dislikeCount: 0
    }
  },
  name: 'FilmApp',
  components: {
    Film
  },
  methods: {
    addFilm() {
      this.index++
    },
    updateLike(isLiked) {
      if (isLiked) {
        this.likeCount++
      }
      else {
        this.likeCount--
      }
    },
    updateDislike(isDisliked) {
      if (isDisliked) {
        this.dislikeCount++
      }
      else {
        this.dislikeCount--
      }
    }
  }
}
</script>

<style>
div {
  padding-bottom: 0.25cm;
  padding-top: 0.25cm;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 30px;
}
button {
  border-color: lightsteelblue;
  background-color: transparent;
  border-width: 0.1cap;
}
span {
  margin-left: 0.5cm;
  margin-right: 0.5cm;
}
</style>
