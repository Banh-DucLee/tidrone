<template>
    <a :href="link" target="_blank" :alt="'Lien vers ' + socialName" class="social-icon-link">
        <img :src="svgUrl" :alt="'Logo de ' + socialName" class="social-icon">
    </a>
</template>

<script setup>
defineProps({
    svgUrl: {
        type: String,
        required: true,
    },
    link: {
        type: String,
        required: true,
    },
    socialName: {
        type: String,
        required: true,
    }
});
</script>

<style scoped>
.social-icon-link {
    display: block;
    aspect-ratio: 1;
    width: 50px;
    height: auto;
}

.social-icon {
    z-index: -1;
    width: 100%;
    height: 100%;
}
</style>