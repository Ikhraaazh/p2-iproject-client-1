<template>
  <div v-if="isLoading" style="display: flex; justify-content: center; align-items:center" > 
    <img src="https://pa1.narvii.com/6148/b21e9bc8b98332750d57296dbaf0d606d49fa5ee_hq.gif" alt="">
  </div>
  <section v-else class="Movies">
    <div class="content">
      <!-- <img v-if="isLoading" src="https://upload.wikimedia.org/wikipedia/commons/b/b1/Loading_icon.gif?20151024034921" alt=""> -->
      <card v-for="movie in movies" :key="movie.id" :movie="movie" />
    </div>
  </section>
  <!-- <div class="container mt-3">
    <div class="row mt-3">
      <card v-for="movie in movies" :key="movie.id" :movie="movie" />
    </div>
    <div class="container d-flex text-align-center justify-content-center">
      <nav aria-label="Page navigation example" class="mt-5">
        <ul class="pagination">
          <li class="page-item">
            <a class="page-link" style="color: #ff9900" href="#">Previous</a>
          </li>

          <li class="page-item">
            <a class="page-link" style="color: #ff9900">1</a>
          </li>

          <li class="page-item" >
            <a class="page-link" style="color: #ff9900" href="#">Next</a>
          </li>
        </ul>
      </nav>
    </div>
  </div> -->
</template>

<script>
import card from "../components/movieCard.vue"
import { mapActions, mapWritableState } from 'pinia';
import { useProjectStore } from '../stores/store';

export default {
  components: {
    card
  },
  methods: {
    ...mapActions(useProjectStore, ['fetchMovies'])
  },
  computed: {
    ...mapWritableState(useProjectStore, ['movies', 'page', 'isLoading'])
  },
  created() {
    this.fetchMovies()
  }
}
</script>