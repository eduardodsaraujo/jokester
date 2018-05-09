<template>
  <div id="app" class="container-fluid mt-4 bg-dark text-white">
    <h3><b>Got jokes?</b></h3>
    <div class="my-2">
      <button class="btn btn-success" @click="addJoke">Add a Joke</button>
      <button class="btn btn-danger" @click="initJokes">Add Ten Random Jokes</button>
    </div>
    <span v-for="type in types">
      <input type="checkbox"
         :value=type
         v-model="checkedTypes"
         checked>
      <label class="mr-2">{{ type }} </label>
    </span>
    <hr>
    <div class="row mt-1">
      <Joke
        v-for="(joke,index) in $store.state.jokes"
        v-show="checkedTypes.includes(joke.type)"
        :joke = "joke"
        :index = "index"
        v-bind:key = "index"/>
    </div>
    </div>
  </div>

</template>

<script>
import { mapActions } from 'vuex'
import Joke from './Joke.vue'

export default{
  data(){
    return {
      types: ['general', 'knock-knock', 'programming'],
      checkedTypes: ['general', 'knock-knock', 'programming']
    }
  },
  methods: mapActions([
    'initJokes',
    'addJoke'
  ]),
  components: {
    Joke
  }
}

</script>

