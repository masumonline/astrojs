<template>
  <section class="text-gray-600 body-font">
  <div class="container px-5 py-24 mx-auto">
    <div class="flex flex-wrap -m-4">
      <div v-for="photo in photos" class="p-4 md:w-1/3">
        <div class="h-full border-2 border-gray-200 border-opacity-60 rounded-lg overflow-hidden">
          <img class="lg:h-48 md:h-36 w-full object-cover object-center" :src="photo.urls.thumb" alt="blog">
          <div class="p-6">
            <h2 class="tracking-widest text-xs title-font font-medium text-gray-400 mb-1">ID: {{photo.id}}</h2>
            <h1 class="title-font text-lg font-medium text-gray-900 mb-3">{{photo.blur_hash}}</h1>
            <p class="leading-relaxed mb-3"> {{photo.title}}</p>  
          </div>
        </div>
      </div>
      
    </div>
  </div>
</section>
</template>

<script lang="ts">
export default {
  data() {
    return {
      name: "Masum",
      photos: []
    };
  },

  async mounted() {
    const response = await fetch("https://api.unsplash.com/photos?page=1&client_id=BJESsq7e9HMRiyuzRD5aKCxwMY1Xf3SZNJHQPhgauRM", {
      method: "GET",
      headers: {
        Authorization: 'SVDmjikADqa8CZhaJqkH4aV2L1ZDwpG2zpFCdKK98fM'
      }
    });
    this.photos = await response.json();
    console.log(this.photos);
  },
};
</script>
