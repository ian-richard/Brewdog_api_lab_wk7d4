<template lang="html">
  <div id="selected_beer">
      <h2> {{selectedBeer.name}} </h2>
      <h3> {{selectedBeer.tagline}} </h3>
      <img class="bottle_img" :src="selectedBeer.image_url" />
  </div>

</template>

<script>
export default {
    name: 'beer-detail',
    props: ['selectedBeer'],

}
</script>

<style>
.bottle_img{
    width: 50px;
}
</style>