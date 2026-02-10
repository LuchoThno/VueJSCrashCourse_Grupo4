<script setup>
import { ref } from 'vue'

const form = ref({ name: '', email: '', message: '' })

const submitForm = () => {
    alert('Gracias por tu mensaje. Te contactaremos pronto.')
    form.value = { name: '', email: '', message: '' }
}
</script>

<template>
    <section class="contact">
        <div class="contact__content">
            <h1>Contáctanos</h1>
            <p>¿Tienes preguntas sobre nuestras rutas o equipamiento? Escríbenos y te responderemos a la brevedad.</p>

            <form class="contact__form" @submit.prevent="submitForm">
                <div class="form__group">
                    <label for="name">Nombre</label>
                    <input type="text" id="name" v-model="form.name" required>
                </div>
                <div class="form__group">
                    <label for="email">Email</label>
                    <input type="email" id="email" v-model="form.email" required>
                </div>
                <div class="form__group">
                    <label for="message">Mensaje</label>
                    <textarea id="message" v-model="form.message" rows="5" required></textarea>
                </div>
                <button type="submit" class="contact__cta">Enviar Mensaje</button>
            </form>
        </div>
    </section>
</template>

<style scoped>
.contact {
    max-width: 1200px;
    margin: 0 auto;
    padding: 8rem 1.5rem 5rem;
}

.contact__content {
    max-width: 720px;
}

h1 {
    font-family: "Fraunces", serif;
    font-size: clamp(2rem, 4vw, 3rem);
    margin-bottom: 1rem;
}

p {
    margin-bottom: 2rem;
    color: #2f3b32;
}

.contact__form {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
}

.form__group {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
}

label {
    font-weight: 600;
}

input,
textarea {
    padding: 0.75rem;
    border: 1px solid rgba(18, 23, 19, 0.2);
    border-radius: 8px;
    font-family: inherit;
    font-size: 1rem;
}

input:focus,
textarea:focus {
    outline: none;
    border-color: var(--color-canyon);
}

.contact__cta {
    background: var(--color-forest);
    color: var(--color-white);
    padding: 0.85rem 1.6rem;
    border-radius: 999px;
    font-weight: 600;
    border: none;
    cursor: pointer;
    align-self: flex-start;
}

.contact__cta:hover {
    transform: translateY(-1px);
    box-shadow: var(--shadow-soft);
}
</style>
