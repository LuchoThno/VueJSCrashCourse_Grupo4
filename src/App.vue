<script setup>
import Navbar from './components/Navbar.vue'
import Footer from './components/Footer.vue'
</script>

<template>
    <header class="header">
        <Navbar />
    </header>

    <main>
        <RouterView />
    </main>

    <Footer />
</template>

<style scoped>
.header {
    position: sticky;
    top: 0;
    z-index: 10;
}

main {
    display: block;
}
</style>
