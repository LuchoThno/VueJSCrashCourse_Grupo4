<script setup>
import GearCard from '@/components/GearCard.vue'

const gearItems = [
    { id: 'mochila', title: 'Mochila', description: 'Elige una mochila de 30-40 litros para salidas de un día, o 50-70 litros para travesías de varios días. Debe tener buen sistema de ajuste y distribución de peso en cintura y hombros.' },
    { id: 'calzado', title: 'Calzado', description: 'Botas de trekking con buen agarre y soporte de tobillo. Impermeables si es posible. Llévalas usadas, nunca estrenes calzado en la montaña para evitar ampollas.' },
    { id: 'capas', title: 'Sistema de Capas', description: 'Primera capa térmica que aleje la humedad, segunda capa aislante (polar o pluma), tercera capa impermeable y cortaviento. La clave está en poder regular tu temperatura.' },
    { id: 'bastones', title: 'Bastones de Trekking', description: 'Reducen el impacto en rodillas y tobillos hasta un 25%. Ajustables en altura, con sistemas de bloqueo confiables y puntas de carburo para terreno rocoso.' },
    { id: 'hidratacion', title: 'Hidratación', description: 'Mínimo 2 litros de agua por persona. Botellas térmicas o sistema de hidratación tipo camelbak. Considera pastillas purificadoras si la ruta tiene fuentes naturales.' },
    { id: 'proteccion', title: 'Protección Solar', description: 'Protector solar FPS 50+, bálsamo labial con protección UV, gorro con visera y lentes de sol con protección UV400. En altura, la radiación solar se intensifica considerablemente.' },
    { id: 'navegacion', title: 'Navegación', description: 'GPS o aplicación móvil con mapas descargados offline, más mapa físico y brújula como respaldo. No confíes solo en la batería de tu teléfono.' },
    { id: 'emergencia', title: 'Kit de Emergencia', description: 'Botiquín básico, silbato, linterna frontal con baterías extra, encendedor, manta térmica y navaja multiuso. Ocupa poco espacio pero puede salvarte la vida.' }
]

const gearImages = [
    { title: 'Mochila', image: '/mochila.jpg', alt: 'Mochila de trekking' },
    { title: 'Calzado', image: '/calzado.jpg', alt: 'Botas de trekking' },
    { title: 'Sistema de Capas', image: '/capas.jpg', alt: 'Sistema de capas de ropa' },
    { title: 'Bastones', image: '/bastones.jpg', alt: 'Bastones de trekking' },
    { title: 'Hidratación', image: '/hidratacion.jpg', alt: 'Sistema de hidratación' },
    { title: 'Protección Solar', image: '/proteccion.jpg', alt: 'Protección solar y lentes' },
    { title: 'Navegación', image: '/navegacion.jpg', alt: 'GPS y herramientas de navegación' },
    { title: 'Kit de Emergencia', image: '/emergencia.jpg', alt: 'Kit de emergencia' }
]
</script>

<template>
    <section class="gear">
        <div class="gear__intro">
            <h1 class="gear__title">Equipamiento Esencial</h1>
            <p class="gear__description">Prepararse adecuadamente es clave para disfrutar la montaña de forma segura.
                Aquí encontrarás el equipo fundamental que no puede faltar en tu mochila.</p>
        </div>

        <div class="gear__content">
            <article v-for="item in gearItems" :key="item.id" class="gear__item" :id="item.id">
                <h2 class="gear__item-title">{{ item.title }}</h2>
                <p class="gear__item-text">{{ item.description }}</p>
            </article>
        </div>

        <div class="gear__carousel">
            <h2 class="gear__carousel-title">Galería de Equipamiento</h2>
            <div class="gear__carousel-track">
                <GearCard v-for="img in gearImages" :key="img.title" :title="img.title" :image="img.image"
                    :image-alt="img.alt" />
            </div>
        </div>
    </section>
</template>

<style scoped>
@import '@/assets/css/gear.css';
</style>
