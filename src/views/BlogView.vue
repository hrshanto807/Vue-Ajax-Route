<script setup>
import { RouterLink } from "vue-router";
import { onBeforeMount } from "vue";
import { ref } from "vue";

const blogPosts = ref([]);

const allPosts = ref([]);
const offset = ref(0);
const limit = 9;

onBeforeMount(async () => {
    const response = await fetch('https://jsonplaceholder.typicode.com/posts');
    blogPosts.value = await response.json();

    allPosts.value = blogPosts.value;
        //   6 post
    blogPosts.value = blogPosts.value.slice(0, 9);

});

const loadMore = () => {
    offset.value += limit;
    const nextPosts = allPosts.value.slice(offset.value, offset.value + limit);
    blogPosts.value = [...blogPosts.value, ...nextPosts];
}


</script>

<template>
    <div class="flex justify-center flex-col items-center">
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <!-- Blog Post Cards -->
        <article v-for="post in blogPosts" :key="post.id"
            class="bg-white rounded-lg shadow-md overflow-hidden hover:shadow-lg transition duration-200">
            <img :src="`https://picsum.photos/800/400?random=${post.id}`" alt="Blog post"
                class="w-full h-48 object-cover">
            <div class="p-6">
                <div class="flex items-center mb-3">
                    <img src="https://picsum.photos/32/32?random=2" alt="Author" class="w-8 h-8 rounded-full mr-3">
                    <span class="bg-blue-100 text-blue-800 text-xs font-medium px-2.5 py-0.5 rounded">Programming</span>
                </div>
                <h2 class="text-xl font-semibold text-gray-800 mb-2">{{ post.title }}</h2>
                <p class="text-gray-600 mb-4">{{ post.body }}</p>
                <div class="flex items-center justify-between">
                    <span class="text-sm text-gray-500">5 min read</span>
                    <!-- <a href="single.html" class="text-blue-500 hover:text-blue-600 font-medium">Read More →</a> -->
                    <RouterLink :to="`/blog/${post.id}`" class="text-blue-500 hover:text-blue-600 font-medium">Read More
                        →</RouterLink>
                </div>
            </div>
        </article>       
    </div>
    <button type="button" class="bg-blue-500 text-white px-6 py-3 rounded-lg hover:bg-blue-600 transition duration-200 m-4" @click="loadMore">Load More</button>
    </div>

   

</template>

<style scoped></style>
