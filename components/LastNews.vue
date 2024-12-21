<template>
    <section class="last-news-section">
        <h2 class="title-2 text-center">Nos Actualités</h2>
        <div class="news-list">
            <NewsPreview v-for="(article, index) in articles" :key="index" :article="article" />
        </div>
        <Button to="/news" text="Voir plus" buttonClass="button-typo-medium" />
    </section>
</template>

<script>
    export default {
        data() {
            return {
                articles: []
            };
        },
        async mounted() {
            const response = await fetch('https://cms.duclee-playground.fr/wp-json/wp/v2/posts?per_page=3&orderby=date&order=desc');
            this.articles = await response.json();
        }
    };
</script>

<style scoped>
    .last-news-section {
        width: 100%;
        display: flex;
        flex-flow: column nowrap;
        justify-content: center;
        align-items: center;
        padding: 16px;
        gap: 16px;
        box-sizing: border-box;
    }

    .news-list {
        display: flex;
        flex-flow: row nowrap;
        justify-content: center;
        align-items: center;
        gap: 8px;
    }
</style>