<template>
  <h1>영화정보</h1>
  
  <div v-for="(movie, i) in movies" :key="i" class="item">
    <figure>
      <img :src="movie.imgUrl" :alt="movie.title">
    </figure>
    <div class="info">
      <h3 class="bg-yellow">제목: {{ movie.title }}</h3>
      <p>개봉년도: {{ movie.year }}</p>
      <p>장르: {{ movie.category }}</p>
      <button @click="increaseLike(i)">좋아요</button> <span>{{ movie.like }}</span>
      <p>
        <button @click="isModal = true">상세정보</button>
      </p>
    </div>
    <!-- <p v-for="(food, i) in foods" :key="i">{{ food }}</p> -->
  </div>
  <div class="modal" v-if="isModal">
    <div class="inner">
      <h3>Detail</h3>
      <p>영화 상세정보</p>
      <button @click="isModal = false">닫기</button>
    </div>
  </div>
</template>

<script>

import movies from './assets/movies'
console.log('movies: ', movies);

  export default {
    name: 'App',
    data() {
      return {
        // foods: ['김밥', '만두', '순대'],
        isModal: false,
        movies: movies,
      }
    },
    methods: {
      increaseLike(i) {
        this.data[i].like += 1;
      }
    }
  }

</script>

<style>
  .bg-yellow {
    background-color: gold;
  }
  * {
    box-sizing:  border-box;
    margin: 0%;
  }
  body {
    max-width: 768px;
    margin: 0 auto;
    padding: 20px;
  }
  h1, h2, h3 {
    margin-bottom: 1rem;
  }
  p {
    margin-bottom: 0.5rem;
  }
  button {
    margin-top: 10px;
    margin-right: 1rem;
  }
  .item {
    width: 100%;
    border: 1px solid #ccc;
    display: flex;
    margin-bottom: 20px;
    padding: 1rem;
  }
  .item figure {
    width: 30%;
    margin-right: 1rem;
  }
  .item img {
    width: 100%;
  }
  .item .info {
    width: 100%;
  }
  .modal {
    background: rgba(0, 0, 0, 0.7);
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .modal .inner {
    background: #fff;
    width: 80%;
    padding: 20px;
    border-radius: 10px;
  }
</style>
