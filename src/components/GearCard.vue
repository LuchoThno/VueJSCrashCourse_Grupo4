<script setup>
defineProps({
    title: { type: String, required: true },
    description: { type: String, required: true },
    image: { type: String, required: true },
    imageAlt: { type: String, default: '' }
})
</script>

<template>
    <a href="#" class="gear__carousel-item">
        <img :src="image" :alt="imageAlt" class="gear__carousel-img">
        <p class="gear__carousel-caption">{{ title }}</p>
    </a>
</template>
