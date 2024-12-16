<template>
    <a class="shadow-base" :href="data.link">
        <article>
            <img :src="data.imageUrl" :alt="data.altImage" class="service-preview-image">
            <h3 class="title-3">{{ data.title }}</h3>
            <p class="paragraph-regular">{{ data.description }}</p>
        </article>
        <div class="link-wrapper">
                <p class="link-typo">En savoir plus</p>
                <img class="service-preview-arrow" src="/images/svg/arrow-right.svg">
        </div>
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
        display: flex;
        flex-flow: column nowrap;
        align-items: start;
        justify-content: space-between;
        padding: 8px;
        text-decoration: none;
        color: var(--color-main-black);
        border: 1px solid var(--color-opacity-black-10);;
    }

    article {
        display: flex;
        flex-flow: column nowrap;
        gap: 24px;
    }

    .service-preview-image {
        width: 100%;
        object-fit: cover;
    }

    .link-wrapper {
        display: flex;
        flex-flow: row nowrap;
        align-items: center;
        justify-content: left;
        gap: 16px;
    }

    .service-preview-arrow {
        width: 42px;
    }
</style>