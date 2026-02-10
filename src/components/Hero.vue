<script setup>
import { RouterLink } from 'vue-router'
</script>

<template>
    <section class="hero" aria-labelledby="hero-title">
        <img class="hero__image" src="/Hero.png" alt="Montana iluminada por el sol al amanecer">
        <div class="hero__inner">
            <div class="hero__content">
                <p class="hero__eyebrow">Crash Course Montañas</p>
                <h1 id="hero-title" class="hero__title">Una cima, mil historias</h1>
                <p class="hero__subtitle">Explora rutas guiadas y paisajes que se quedan contigo.</p>
                <RouterLink class="hero__cta" to="/routes">Ver rutas</RouterLink>
            </div>
        </div>
    </section>
</template>
