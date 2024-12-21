<template>
    <article class="service-details-container">
        <img :src="data.imageUrl" :alt="data.altImage" class="service-details-image">
        <div class="service-details-text">
            <h4 class="title-4 text-center service-details-title">{{ data.title }}</h4>
            <div class="service-details-infos">
                <p class="text-sm service-details-description">{{ data.description }}</p>
                <span class="separator"></span>
                <div class="actions-container">
                    <ul v-for="(actionGroup, index) in data.actionsGroup" :key="index" class="actions-group">
                        <p v-if="actionGroup.groupTitle !== ''" class="text-sm text-bold"> {{ actionGroup.groupTitle }}</p>
                        <div class="actions-group-items">
                            <li v-for="(action, index) in actionGroup.actions" :key="index" class="text-sm text-center action-item">{{ action }}</li>
                        </div>
                    </ul>
                </div>
                <div class="service-details-cta">
                    <p class="text-sm">Cette prestation vous intéresse ? Contactez-moi directement pour plus d’informations</p>
                    <Button text="Demander un devis" to="/contact" buttonClass="button-typo-medium" />
                </div>
            </div>
        </div>
    </article>

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
    .service-details-container {
        display: flex;
        flex-flow: row nowrap;
    }

    .service-details-image {
        max-width: 33%;
        object-fit: cover;
    }

    .service-details-text {
        display: flex;
        flex-flow: column nowrap;
        box-sizing: border-box;
    }

    .service-details-title {
        padding: 12px 0;
        flex: 1;
        background-color: var(--color-opacity-black-20);
    }

    .service-details-description {
        padding: 12px;
    }

    .separator {
        content: '';
        display: block;
        width: 95%;
        margin: 0 auto;
        border: 1px solid var(--color-opacity-black-25);
    }

    .actions-container {
        display: flex;
        flex-flow: column nowrap;
        padding: 8px 16px;
        gap: 8px;
    }

    .actions-group {
        display: flex;
        max-height: 20%;
        flex-flow: column wrap;
        justify-content: space-between;
        align-items: center;
        margin: 0;
        padding: 0 8px;
        gap: 8px;
    }

    .actions-group-items {
        display: flex;
        width: 100%;
        flex-flow: row wrap;
        justify-content: space-between;
        align-items: start;
        margin: 0;
        gap: 4px;
    }

    .action-item {
        width: 30%;
        max-width: 30%;
        list-style-position: inside;
    }

    .service-details-cta {
        display: flex;
        flex-flow: row nowrap;
        align-items: center;
        justify-content: space-between;
        gap: 8px;
        padding: 8px;
    }

    @media (width <= 768px) {
        .service-details-container {
            flex-direction: column;
        }

        .service-details-image {
            width: 100%;
        }
    }

</style>