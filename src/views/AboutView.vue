<script setup>

import {ref} from "vue";

const Teams = ref([
  {
    id: 1,
    name: "John Doe",
    role: "Web Developer",    
    bio: "I'm a passionate web developer with a love for creating beautiful and functional websites.",},
  {
    id: 2,
    name: "Jane Smith",
    role: "UI/UX Designer",
    bio: "I'm a skilled UI/UX designer with a keen eye for design and a passion for user experience.",
  },
  {
    id: 3,
    name: "John Doe",
    role: "Web Developer",    
    bio: "I'm a passionate web developer with a love for creating beautiful and functional websites.",
  }
]);

</script>

<template>
       
            <!-- About Section -->
            <section class="bg-white rounded-lg shadow-md overflow-hidden mb-8">
                <div class="p-8">
                    <h1 class="text-3xl font-bold text-gray-800 mb-6">About Us</h1>
                    <p class="text-gray-600 mb-6">Welcome to My Blog, a platform dedicated to sharing knowledge and insights about web development, design, and technology. Our mission is to create a community where developers and designers can learn, grow, and connect with like-minded individuals.</p>
                    <p class="text-gray-600 mb-6">Founded in 2024, we've been committed to providing high-quality content that helps our readers stay up-to-date with the latest trends and best practices in the industry.</p>
                </div>
            </section>

            <!-- Team Section -->
            <section class="mb-8">
                <h2 class="text-2xl font-bold text-gray-800 mb-6">Our Team</h2>
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                    <!-- Team Member  -->
                    <div class="bg-white rounded-lg shadow-md overflow-hidden" v-for="Team in Teams" :key="Team.id">
                        <img :src=" `https://picsum.photos/400/400?random=${Team.id}` " alt="Team member" class="w-full h-64 object-cover">
                        <div class="p-6">
                            <h3 class="text-xl font-semibold text-gray-800 mb-2">{{ Team.name }}</h3>
                            <p class="text-gray-600 mb-4">{{ Team.role }}</p>
                            <p class="text-gray-600">{{ Team.bio }}</p>
                        </div>
                    </div>
                </div>
            </section>
       
</template>

<style scoped></style>
