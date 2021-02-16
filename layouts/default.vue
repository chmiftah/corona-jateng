<template>
  <div>
    <div>
      <Header />
    </div>

     <nuxt/>
     <section>
        <div class="bg-green-600 p-6 text-center text-white">
          copyright-2021
        </div>
      </section>
  </div>
</template>

<script>
import Header from '@/components/Header.vue'
export default {
  components:{
    Header
  }

}
</script>

