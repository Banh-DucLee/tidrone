<template>
    <a class="shadow-base" :href="data.link">
        <article>
            <div class="service-preview-image-wrapper">
                <img :src="data.imageUrl" :alt="data.altImage" class="service-preview-image">
                <span class="service-preview-image-mask"></span>
                <span class="divider"></span>
            </div>
            <div class="service-preview-content">
                <h3 class="title-3 service-preview-title">{{ data.title }}</h3>
                <p class="paragraph-regular">{{ data.descriptionPreview }}</p>
                <div class="link-wrapper">
                    <p class="link-typo">En savoir plus</p>
                    <img class="service-preview-arrow" src="/images/svg/arrow-right.svg" alt="Image d'une fléche">
                </div>
            </div>
        </article>
    </a>
</template>

<script setup>
    defineProps({
        data: {
            type: Object,
            required: true
        }
    });
</script>

<style scoped>
@import 'assets/css/variables.css';
    a {
        flex: 1;
        text-decoration: none;
        color: var(--color-main-black);
        transition: all 0.2s ease-in-out;
    }

    a:hover {
        scale: 1.015;
    }

    a:hover .divider {
        height: 10px;
    }

    a:hover .service-preview-image-mask:after {
        opacity: 0;
    }

    article {
        display: flex;
        flex-flow: column nowrap;
        justify-content: center;
        align-items: center;
        width: 100%;
        height: 100%;
    }

    .service-preview-image-wrapper {
        position: relative;
        height: auto;
        width: 100%;
        aspect-ratio: 21/9;
    }

    .service-preview-image {
        width: 100%;
        height: auto;
        aspect-ratio: 21/9;
        object-fit: cover;
    }

    .service-preview-image-mask {
        content: '';
        display: block;
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: radial-gradient(var(--color-opacity-black-10), var(--color-opacity-black-50));
    }

    .service-preview-image-mask:after {
        content: '';
        display: block;
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: var(--color-opacity-black-40);
        opacity: 1;
        transition: opacity 0.3s ease-in-out;
    }

    .divider {
        position: absolute;
        content: '';
        display: block;
        bottom: 0;
        width: 100%;
        height: 5px;
        background-color: var(--color-primary-500);
        transition: all 0.2s ease-in-out;
    }

    .service-preview-content {
        flex: 1;
        display: flex;
        flex-flow: column nowrap;
        justify-content: space-between;
        gap: 8px;
        background-color: var(--color-opacity-black-10);
        padding: 8px 8px 0px 8px;
    }

    .link-wrapper {
        display: flex;
        flex-flow: row nowrap;
        align-self: end;
        align-items: center;
        justify-content: left;
        gap: 16px;
    }

    .service-preview-arrow {
        width: 42px;
    }
</style>