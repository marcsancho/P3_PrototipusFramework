<template>
  <div id="carouselExampleAutoplaying" class="carousel slide" data-bs-ride="true">
    <div class="carousel-inner">
      <div v-for="slide in this.array" :key="slide.id" v-bind:class="(slide.id == array[0].id)?'carousel-item active':'carousel-item'">
        <img :src="slide.urls.regular" class="d-block w-100" alt="hola">
      </div>
    </div>
    <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleAutoplaying" data-bs-slide="prev">
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Previous</span>
    </button>
    <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleAutoplaying" data-bs-slide="next">
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="visually-hidden">Next</span>
    </button>
  </div>
</template>

<script>
export default {
  name: "Carousel",
  data() {
    return{
      array: [],
    }
  },
  async created() {
    try {
      const promise = await this.$unsplash.random(3, 'landscape');
      console.log(promise);
      this.array = promise;
    } catch (error) {
      console.log(error);
    }
  }
}
</script>
