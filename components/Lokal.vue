<template>
  <div class="p-6">
     <nuxt-link :to="{ name: routeName, params: { id: id } }">
    <div class="border border-gray-300 bg-white shadow-lg p-6">
    <div class="flex ">
       <div class="w-2/3">

      <div class="text-green-500 font-semibold text-3xl mb-4">{{title}} </div>
      <span class="text-gray-500">{{ published }}</span> - <span class="text-gray-500">{{author}}</span>
      <div class="mt-2 text-1xl font-semibold">{{content|truncate(20)}}</div>

      <div class="font-semibold text-xl text-blue-600 mt-6">Baca Selanjutnya</div>
     </div>

      <div class="hidden md:block w-1/3 pl-8">
        <img :src="image" alt="" class="w-full h-64 rounded-lg shadow-md">
      </div>
    </div>
    </div>
     </nuxt-link>
  </div>
</template>

<script>
export default {
props:[
  "id",
  "author",
  "content",
  "title",
  "image",
  "published"
],
 filters: {
            truncate: function(value) {
                if (value && value.length > 200) {
                    value = value.substring(0, 197) + '...';
                }
                return value
            }
        },
   computed: {
    routeName() {
      return "berita-details-id";
    },


}
}

</script>

<style>

</style>