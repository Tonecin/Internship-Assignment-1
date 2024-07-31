<template>
  <div v-show="!deleted" :class="{liked: liked, disliked, disliked}">
  
    <div>
      <span>
        <button @click="deleteFilm">Delete</button>
      </span>
      {{ film.title }} ( {{ film.year }} )
      <span>
        <button @click="like" 
        :disabled="disliked" 
        :class="{liked: liked}">{{ likeText }}</button>
      </span>
      <span>
        <button @click="dislike" 
        :disabled="liked"
        :class="{disliked: disliked}">{{ dislikeText }}</button>
      </span>
    </div>

    <div class="actors">
      <Actor v-for="item in film.actors.slice(0, index)" :actor = "item"/>
      <div>
        <button @click="addActor" v-show="index < film.actors.length">Add Actor</button>
      </div>
    </div>

  </div>
</template>
  
<script>
import Actor from './Actor.vue'

export default {
  data() {
    return {
      index: 3,
      deleted: false,
      liked: false,
      disliked: false,
      likeText: "Like",
      dislikeText: "Dislike"
    }
  },
  props: ['film'],
  methods: {
    deleteFilm() {
      this.deleted = true
    },
    addActor() {
      this.index++
    },
    like() {
      this.liked = !this.liked
      this.$emit('like-change', this.liked)
      if (this.liked) {
        this.likeText = "Liked"
      }
      else {
        this.likeText = "Like"
      }
    },
    dislike() {
      this.disliked = !this.disliked
      this.$emit('dislike-change', this.disliked)
      if (this.disliked) {
        this.dislikeText = "Disliked"
      }
      else {
        this.dislikeText = "Dislike"
      }
    }
  },
  components: {
      Actor
  }
};
</script>
  
<style scoped>
  div.actors {
    padding-left: 1cm;
  }
  div.liked {
    background-color: lightblue;
  }
  div.disliked {
    background-color: lightsalmon;
  }
  button.liked {
    background-color: blue;
    color: white;
  }
  button.disliked {
    background-color: orange;
    color: white;
  }
</style>