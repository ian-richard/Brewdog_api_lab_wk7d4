<template>
  <div id="favourite_beers">
      <h2>Favourite Beers</h2>
      <ul>
          <li v-for="favouriteBeer in favouriteBeers" :key="favouriteBeer.id"> {{favouriteBeer.name}}  <img :src="favouriteBeer.image_url" class="bottle_img"/>
          <button>Remove from favourites</button></li>
      </ul>


  </div>
</template>

<script>
export default {
    name: 'favourite-beer',
    props: ['favouriteBeers'],
    methods: {
        removeFromFavourites(){
    this.favouriteBeers.splice(favouriteBeer.index)
  },
    }

}
</script>

<style>
#favourite_beers {
    flex-direction: column;
}
</style>