<template>
    <NuxtLink v-if="buttonType === 'redirect'" class="button-component"  :to="to" :class="buttonStyle">{{ text }}</NuxtLink>
    <a v-else-if="buttonType === 'mail'" class="button-component"  :href="`mailto:${to}`" :class="buttonStyle" target="_blank">{{ text }}</a>
</template>

<script setup>
defineProps({
    buttonType: {
        type: String,
        default: 'redirect',
        validator: (value) => ['redirect', 'mail'].includes(value)
    },
    text: {
        type: String,
        required: true,
    },
    to: {
        type: String,
        required: true,
    },
    buttonStyle: {
        type: String,
        required: true,
    }
});
</script>

<style scoped>
    .button-component {
        text-decoration: none;
        color: var(--color-main-black);
        border: 2px solid var(--color-main-black);
        padding: 5px 10px;
        border-radius: 5px;
    }

    .button-component:hover {
        color: var(--color-primary-800);
        border-color: var(--color-primary-800);
    }
</style>