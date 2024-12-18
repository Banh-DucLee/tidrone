<template>
    <main>
        <section class="landing-section">
            <h1 class="title-1 text-center">Explorez vos projets sous un nouvel angle</h1>
            <p class="paragraph-regular text-center landing-section-subheadline">
                De l'inspection industrielle à la prise de vue cinématographique, en passant par les images immersives en drone FPV, nous offrons des solutions aériennes innovantes et sur-mesure pour tous vos projets.
                <br>Homologué pour les scénarios européen S1, S2 et S3
            </p>
            <Button text="Demander un devis" to="/contact" buttonClass="button-typo-large"/>
            <iframe class="landing-section-video"
                    height="100%"
                    src="https://www.youtube.com/embed/ndTZAj9abSw?autoplay=1&mute=1&loop=1&playlist=ndTZAj9abSw&controls=0&disablekb=1&showinfo=0"
                    title="FPV cinématique"
                    frameborder="0"
                    allow="autoplay; encrypted-media"
                    allowfullscreen
            ></iframe>
            <span class="landing-section-video-mask"></span>
        </section>
        <section class="services-section">
            <h2 class="title-2 text-center">Nos Services</h2>
            <div class="services-section-preview">
                <ServicePreview v-for="(service, index) in services" :key="index" :data="service" />
            </div>
        </section>
    </main>
</template>

<script setup>
    import servicesData from 'assets/json/services.json';
    const services = servicesData;
</script>

<style scoped>
.landing-section {
    color: var(--color-main-white);
    position: relative;
    display: flex;
    flex-flow: column nowrap;
    align-items: center;
    justify-content: center;
    height: 60vh;
    width: 100%;
    padding-inline: 16px;
    box-sizing: border-box;
    gap: 36px;
    margin: 36px 0;
    overflow-x: hidden;
}

.landing-section-subheadline {
    max-width: 800px;
}

.landing-section-video {
    position: absolute;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
    z-index: -1;
    height: 100%;
    object-fit: cover;
    aspect-ratio: 21/9;
}

.landing-section-video-mask {
    content: '';
    display: block;
    background-color: var(--color-opacity-black-40);
    position: absolute;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
    z-index: -1;
    height: 100%;
    aspect-ratio: 21/9;
}

.services-section {
    background-color: var(--color-primary-200);
    padding: 24px 0;
    display: flex;
    flex-flow: column nowrap;
    align-items: center;
    gap: 24px;
}

.services-section-preview {
    display: flex;
    flex-flow: row wrap;
    justify-content: center;
    gap: 8px;
    padding-inline: 16px;
}

@media (width <= 768px) {
    .landing-section {
        height: calc(85vh - 80px);
        padding-inline: 16px;
    }

    .services-section-preview {
        flex-direction: column;
    }
}

</style>