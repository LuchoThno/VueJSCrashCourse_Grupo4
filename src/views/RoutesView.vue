<template>
    <section class="routes">
        <div class="routes__content">
            <h1>Nuestras Rutas</h1>
            <p>Descubre las rutas más increíbles de nuestra región. Desde caminatas accesibles hasta expediciones
                desafiantes.</p>

            <div class="routes__grid">
                <article class="route__card">
                    <h2>Ruta del Mirador</h2>
                    <p class="route__difficulty">Dificultad: Fácil</p>
                    <p class="route__description">Una caminata de 2 horas con vistas espectaculares. Ideal para
                        principiantes.</p>
                </article>
                <article class="route__card">
                    <h2>Sendero de los Pinos</h2>
                    <p class="route__difficulty">Dificultad: Media</p>
                    <p class="route__description">Travesía de 4 horas a través de un bosque de pinos centenario.</p>
                </article>
                <article class="route__card">
                    <h2>Cima Principal</h2>
                    <p class="route__difficulty">Dificultad: Alta</p>
                    <p class="route__description">Expedición de día completo hasta la cima más alta de la región.</p>
                </article>
            </div>
        </div>
    </section>
</template>

<style scoped>
.routes {
    max-width: 1200px;
    margin: 0 auto;
    padding: 8rem 1.5rem 5rem;
}

.routes__content {
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

.routes__grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 1.5rem;
}

.route__card {
    background: #ffffff;
    border-radius: 20px;
    padding: 1.5rem;
    box-shadow: 0 16px 40px rgba(16, 23, 18, 0.12);
    border: 1px solid rgba(16, 23, 18, 0.06);
}

.route__card h2 {
    font-family: "Fraunces", serif;
    margin: 0 0 0.5rem;
}

.route__difficulty {
    font-weight: 600;
    color: var(--color-canyon);
    margin-bottom: 1rem;
}
</style>
