<template>
    <a :href="link" target="_blank" :alt="'Lien vers ' + linkName" :style="{ '--icon-size': size }" class="social-icon-link">
        <img :src="logoUrl" :alt="'Logo de ' + linkName" class="social-icon">
    </a>
</template>

<script setup>
defineProps({
    logoUrl: {
        type: String,
        required: true,
    },
    link: {
        type: String,
        required: true,
    },
    linkName: {
        type: String,
        required: true,
    },
    size: {
        type: String,
        default: '50px'
    }
});
</script>

<style scoped>
.social-icon-link {
    display: block;
    aspect-ratio: 1;
    width: var(--icon-size);
    height: auto;
}

.social-icon {
    z-index: -1;
    width: 100%;
    height: 100%;
}
</style>