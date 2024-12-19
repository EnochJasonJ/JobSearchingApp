<script setup>
    import { RouterLink } from 'vue-router';
</script>

<template>
    <section class="text-center flex flex-col justify-center items-center h-96 ">
        <i class="pi pi-exclamation-triangle text-yellow-500 font-bold text-7xl"></i>
        <h1 class="text-5xl font-bold">404 Not Found</h1>
        <p class="text-lg">Page does not exist</p>
        <RouterLink to="/" class="bg-blue-200 px-5 py-1 rounded-md">
            Go Back
        </RouterLink>
    </section>
</template>