<template>
  <section id="details-section">
    <div class="container text-light pt-5">
      <div class="row">
        <div class="col-md-8">
          <h5>Synopsis</h5>
          <span>{{ movie.longDescription }}</span>
          <div class="row my-5">
            <div class="col-6">
              <h5>Cast</h5>
              <ul class="m-0 details-list">
                <li v-for="(cast, index) in movie.topCast" :key="index">{{ cast }}</li>
              </ul>
            </div>
            <div class="col-6">
              <h5>Release Date</h5>
              <p class="m-0 details-list">{{ movie.releaseDate }}</p>
            </div>
          </div>
          <div class="row my-5">
            <div class="col-6">
              <h5>Director</h5>
              <ul class="m-0 details-list">
                <li v-for="(director, index) in movie.directors" :key="index">{{ director }}</li>
              </ul>
            </div>
            <div class="col-6">
              <h5>Advisories</h5>
              <ul class="m-0 details-list">
                <li v-for="(advisory, index) in movie.advisories" :key="index">{{ advisory }}</li>
              </ul>
            </div>
          </div>
        </div>
        <div class="col-md-4">
          <img :src="BASE_IMAGE_URL + movie.poster_path" :alt="movie.title" class="d-none d-md-block">
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    movie: {
      type: Object,
      default: null
    }
  },
  computed: {
    BASE_IMAGE_URL: () => "https://image.tmdb.org/t/p/original/"
  }
};
</script>

<style>
.details-list {
  display: inline;
  list-style: none;
  padding-left: 0;
}

.details-list li {
  display: inline;
}

.details-list li:after {
  content: ", ";
}

.details-list li:last-child:after {
  content: "";
}
</style>
