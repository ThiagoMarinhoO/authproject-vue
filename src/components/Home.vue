<script setup>
import { onMounted } from 'vue';
import { useAuthStore } from '../stores/auth';

const authStore = useAuthStore();

onMounted(async () => {
    await authStore.getUser();
});
</script>

<template>
    <div v-if="authStore.user">
        <h1>{{ authStore.user.name }}</h1>
        <p>{{ authStore.user.email }}</p>
    </div>
    <div v-else class="w-fit mx-auto flex items-center justify-center h-screen">
        <router-link :to="{name: 'Login'}" class="text-gray-800 uppercase text-5xl font-bold px-5 py-2.5 text-center inline-flex items-center">Faça Login</router-link>
    </div>
</template>