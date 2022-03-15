<!-- Please remove this file from your project -->
<template>
<div class="flex flex-wrap px-10">
  <div class="mt-12 mb-5 w-full text-center relative relative flex flex-wrap justify-center">
    <h1 class=" nuestrosAticles z-10 my-6 text-3xl">Nuestros artículos</h1>
    <img class="brushArticle absolute z-0" src="/BRUSH.png" alt="BRUSH">
    <div class="md:flex  space-y-3 md:space-y-0 md:space-x-4 mt-6"></div>
  </div>
	<div class="w-1/4 mt-10 pr-10 md:pl-12 relative">
		<div class="bg-white border shadow-lg rounded-md w-full flex flex-wrap pb-28">
          <CardCategory 
            v-for="(tr, indexTr) in categories" 
            :key="indexTr" :category="tr" 
            @selectCategory="(e) => categorySelect = e"
            :categorySelect="categorySelect"
            />
    </div>
	</div>
	<div class="w-3/4">
		<div class="mx-5 grid grid-cols-1 gap-6 md:grid-cols-2 lg:grid-cols-3 mt-10">
        <CardArticle v-for="(tr, indexTr) in articles" :key="indexTr" :article="tr"  />
    </div>
  </div>
</div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Header',
  data: () => ({
    categorySelect: 'Todos',
    articles: [],
    categories: [
      {
        name: "Todos"
      },
      {
        name: "Productos"
      },
      {
        name: "Recetas"
      },
      {
        name: "Consejos"
      }
    ]
  }),
  watch: {
    categorySelect() {
      this.getArticles();
    }
  },
  methods: {
    getArticles() {
      axios.get('https://5eed24da4cbc340016330f0d.mockapi.io/api/articles', {params: {filter: this.categorySelect == 'Todos' ? '' : this.categorySelect}})
        .then(response => {
          console.log(response.data)
          this.articles = response.data
        })
        .catch(error => {
          console.log(error)
        })
    },
  },
  created(){
    this.getArticles()
  }
}
</script>

<style>
.nuestrosAticles{
  z-index: 10;
  font-family: 'Caveat', cursive;
  font-size: 80px;
  font-weight: 700;
  color: #3F3356;

  @media (max-width: 768px) {
    font-size: 50px;
  }

  @media (max-width: 576px) {
    font-size: 30px;
  }

  @media (max-width: 480px) {
    font-size: 20px;
  }
}
.brushArticle{
  z-index: 0;
  margin-top: 50px;
  margin-right: -50px;
  height: 70px;
  width: 500px;
  opacity: 0.2;
}

</style>
