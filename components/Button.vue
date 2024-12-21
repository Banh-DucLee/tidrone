<template>
    <NuxtLink v-if="buttonType === 'redirect'" class="button-component text-center"  :to="to" :class="buttonClass">{{ text }}</NuxtLink>
    <a v-else-if="buttonType === 'mail'" class="button-component text-center"  :href="`mailto:${to}`" :class="buttonClass" target="_blank">{{ text }}</a>
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
    buttonClass: {
        type: String,
        required: true,
    }
});
</script>

<style scoped>
    .button-component {
        text-decoration: none;
        color: var(--color-primary-500);
        background-color: var(--color-main-transparent);
        border: 5px solid var(--color-primary-500);
        padding: 7px 11px;
        border-radius: 4px;
        box-sizing: border-box;
        text-shadow: 0px 0px 4px var(--color-opacity-black-25);
    }

    .button-component:hover {
        color: var(--color-primary-700);
        border-color: var(--color-primary-700);
    }

    .button-component:active {
        color: var(--color-primary-800);
        border-color: var(--color-primary-800);
    }

    .button-component:disabled {
        color: var(--color-opacity-black-50);
        border-color: var(--color-opacity-black-25);
    }

    .button-component:focus {
        outline-color: var(--color-primary-800);
    }

</style>