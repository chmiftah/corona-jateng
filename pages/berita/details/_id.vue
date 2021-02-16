<template>
  <div class="p-6">
    <div class="bg-gray-100 rounded-lg shadow-md p-6">
       <transition name="fade">
      <div class="loading h-screen center " id="spinner" v-show="loading">

            <div class="loadingspinner">

            </div>

      </div>
    </transition>
        <div v-for="(berita, index) in berita" :key="index">
          <div class="font-bold text-3xl font-sans mb-2">{{berita.title}}</div>
           <div class="text-md font-san font-semibold mb-4 ">{{berita.publishedAt}}</div>
          <img :src="berita.urlToImage" class="h-64 rounded-lg">

          <div class="font-semibold text-lg mt-12 w-3/4 leading-relax ">{{berita.description}}{{berita.content}}</div>
          <div class="font-semibold text-md mt-12 ">author : {{berita.author}}</div>
          <div class="font-semibold text-md ">source: {{ berita.source.name }}</div>
    </div>
  </div>


  </div>
</template>

<script>
import axios from 'axios'
export default {
  data(){
    return{
      loading : false,
      berita :[],

    }
  },
  methods:{
    async fetch(){
      this.loading=true
      let response= await axios.get(`http://newsapi.org/v2/top-headlines?country=id&page=${this.$route.params.id}&pageSize=1&apiKey=3b460804fbc24e2c81d2c90a0aaff1e6`)
      console.log(response.data.articles)
      this.berita=response.data.articles
      this.loading=false
    }
  },
   mounted(){
      console.log(this.$route.params.id)
      this.fetch()
    }
}
</script>
<style>


.loadingspinner {
	pointer-events: none;
	width: 2.5em;
	height: 2.5em;
	border: 0.4em solid transparent;
	border-color: #eee;
	border-top-color: #3E67EC;
	border-radius: 50%;
	animation: loadingspin 1s linear infinite;
}

@keyframes loadingspin {
	100% {
			transform: rotate(360deg)
	}
}

#spinner {
	height: 50vh;
	margin: 0;
	padding: 0;
	display: flex;
	justify-content: center;
	align-items: center;
}

</style>
