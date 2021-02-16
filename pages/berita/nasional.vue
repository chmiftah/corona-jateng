<template>
<div>
   <section class="mt-6 border-b border-gray-300">
          <div class="flex justify-center p-8">
               <nuxt-link to='/berita' class="mx-8 md:mx-12">
              Lokal
            </nuxt-link>
            <nuxt-link to='nasional'  class=" mx-8 md:mx-12">
              Nasional
                </nuxt-link>
            <nuxt-link to="dunia"  class="mx-8 md:mx-12">
              Dunia
                </nuxt-link>
          </div>
  </section>

  <div class=" bg-gray-100 p-6">
    <div class="text-4xl font-semibold px-6">
      Berita Nasional
    </div>
    <transition name="fade">
      <div class="loading h-screen center " id="spinner" v-show="loading">

            <div class="loadingspinner">

            </div>

      </div>
    </transition>
    <Lokal  v-for="(berita, index) in lokal" :key="index"
    :title="berita.title"
    :id="index+1"
    :content="berita.content"
    :author="berita.author"
    :description="berita.description"
    :published="berita.publishedAt"
    :source="berita.source"
    :url="berita.url"
    :image="berita.urlToImage"

    />
    <div class="p-6">

      <button class="w-full bg-blue-500 p-4 rounded-lg focus:outline-none" @click="next">
        <template v-if="readmore">
				Please wait...
			</template>
			<template v-else>
				Load More..
			</template>
      </button>
    </div>





  </div>
  </div>
</template>

<script>
//3b460804fbc24e2c81d2c90a0aaff1e6
import axios from 'axios'
export default {
  data(){
    return {
      loading: false,
      lokal:[],
      maxPerPage :5,
      readmore: false


    }


  },
  methods:{
    next(){
      this.readmore=true
      this.maxPerPage+=5
     setTimeout(()=>{
				this.fetch()

			},1000)

    },

    async fetch(){
      this.loading=true
       this.readmore=false
      let response = await axios.get(`http://newsapi.org/v2/top-headlines?country=id&pageSize=${this.maxPerPage}&apiKey=3b460804fbc24e2c81d2c90a0aaff1e6`)
      console.log(response.data)
      this.lokal = response.data.articles
      this.loading=false

    },
  },

  mounted(){
   //    console.log(this.maxPerPage)
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
