<script setup>
 import { RouterLink } from "vue-router";
  import {onBeforeMount} from "vue";
  import {ref} from "vue";

  const blogPosts = ref([]);

  onBeforeMount(async () => {    
      const response = await fetch('https://jsonplaceholder.typicode.com/posts');
      blogPosts.value = await response.json();

    //   10 post
    blogPosts.value = blogPosts.value.slice(0, 3);
    
  });


</script>

<template>
 
            <!-- Hero Section -->
            <section class="bg-white rounded-lg shadow-md overflow-hidden mb-8">
                <div class="relative">
                    <img src="https://picsum.photos/1200/400?random=20" alt="Hero image" class="w-full h-96 object-cover">
                    <div class="absolute inset-0 bg-black bg-opacity-50 flex items-center justify-center text-center px-4">
                        <div class="text-white">
                            <h1 class="text-4xl md:text-5xl font-bold mb-4">Welcome to My Blog</h1>
                            <p class="text-xl md:text-2xl mb-8">Exploring ideas, sharing knowledge, and connecting with readers</p>
                            <a href="#featured" class="bg-blue-500 text-white px-6 py-3 rounded-lg hover:bg-blue-600 transition duration-200 inline-block">Explore Posts</a>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Featured Posts Section -->
            <section id="featured" class="mb-8">
                <h2 class="text-2xl font-bold text-gray-800 mb-6">Featured Posts</h2>
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                    <!-- Featured Post -->                    
                    <article v-for="post in blogPosts" :key="post.id" class="bg-white rounded-lg shadow-md overflow-hidden hover:shadow-lg transition duration-200">
                    <img :src="`https://picsum.photos/800/400?random=${post.id}`" alt="Blog post" class="w-full h-48 object-cover">
                    <div class="p-6">
                        <div class="flex items-center mb-3">
                            <img src="https://picsum.photos/32/32?random=2" alt="Author" class="w-8 h-8 rounded-full mr-3">
                            <span class="bg-blue-100 text-blue-800 text-xs font-medium px-2.5 py-0.5 rounded">Programming</span>
                        </div>
                        <h2 class="text-xl font-semibold text-gray-800 mb-2">{{ post.title }}</h2>
                        <p class="text-gray-600 mb-4">{{post.body}}</p>
                        <div class="flex items-center justify-between">
                            <span class="text-sm text-gray-500">5 min read</span>
                            <!-- <a href="single.html" class="text-blue-500 hover:text-blue-600 font-medium">Read More →</a> -->
                            <RouterLink :to="`/blog/${post.id}`" class="text-blue-500 hover:text-blue-600 font-medium">Read More →</RouterLink>
                        </div>
                    </div>
                </article>             
                </div>
            </section>
       
</template>
