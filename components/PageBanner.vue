<template>
    <div class="banner-container">
        <img class="banner-image" :src="imageUrl" alt="Banner image">
        <h1 class="title-1 banner-title">{{ title }}</h1>
        <p class="paragraph-regular banner-paragraph">{{ subtitle }}</p>
    </div>
</template>

<script setup>
defineProps({
    title: {
        type: String,
        required: true,
    },
    subtitle: {
        type: String,
        required: true,
    },
    imageUrl: {
        type: String,
        required: true,
    },
});
</script>

<style scoped>
.banner-container {
    position: relative;
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    max-height: 300px;
    padding: 30px 15%;
    gap: 30px;
    box-sizing: border-box;
}

.banner-image {
    object-fit: cover;
    position: absolute;
    z-index: -1;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}

.banner-title {
    text-align: center;
}

.banner-paragraph {
    text-align: center;
}

@media (width <= 768px) {
    .banner-container {
        max-height: none;
    }
}
</style>