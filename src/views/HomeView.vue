<script setup>
    import hero from '@/components/hero.vue'
    import HomeCards from '@/components/HomeCards.vue'
    import JobListings from '@/components/JobListings.vue'
</script>

<template>
    <hero title = "Test Title" subtitle="Test Subtitle" />
    <HomeCards />
    <JobListings :limit="3" :showButton="false" />
</template>