<template>
<div id="app">
    <h1>Brewdog Beers</h1>

    <label for="beer_select"> Select a beer: </label>
    <select id="beer_select" v-model="selectedBeer">
      <option disabled value="">Select a beer</option>
      <option v-for="beer in beers" :key="beer.id" :value="beer"> {{beer.name}} </option>
    </select>

    <button v-if="!favouriteBeers.includes(selectedBeer)" v-on:click="addToFavourites">Add Beer to Favourites</button>

    <beer-detail v-if="selectedBeer" :selectedBeer="selectedBeer"></beer-detail>

    <favourite-beer :favouriteBeers="favouriteBeers"></favourite-beer>



</div>
  
</template>

<script>
import BeerDetail from './components/BeerDetail.vue';
import FavouriteBeer from './components/FavouriteBeer.vue'

export default {
  name: 'App',
  data() {
    return {
      beers: [],
      selectedBeer: null, 
      favouriteBeers: []
    }
  },
  components: {
    'beer-detail': BeerDetail,
    'favourite-beer': FavouriteBeer
  },
    mounted(){
      this.getBeers()
    },
methods: {
  getBeers: function(){
    fetch('https://api.punkapi.com/v2/beers?page=1&per_page=80')
    .then(res => res.json())
    .then(beers => this.beers = beers)
  },
  addToFavourites(){
    this.favouriteBeers.push(this.selectedBeer)
  },
  
  
}
} 

</script>

<style>

</style>