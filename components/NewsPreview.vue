<template>
    <NuxtLink :to="`/article/${article.slug}`">
        <article>
            <div class="image-container">
                <img :src="imageUrl" :alt="'Article sur ' + article.title" />
            </div>
            <div class="content">
                <p class="text-sm">{{ formattedDate }} - Par {{ authorName }}</p>
                <h5 class="title-5">{{ title }}</h5>
            </div>
        </article>
    </NuxtLink>
</template>

<script>
export default {
    props: {
        article: {
            type: Object,
            required: true
        }
    },
    data() {
        return {
            imageUrl: '',
            authorName: '',
        };
    },
    computed: {
        title() {
            return this.article.title.rendered;
        },
        formattedDate() {
            const rawDate = this.article.date;
            return new Date(rawDate).toLocateDateString('fr-FR', {
                day: '2-digit',
                month: '2-digit',
                year: 'numeric',
            });
        },
        articleLink() {
            return `/news/${this.article.slug}`;
        },
    },
    async mounted() {
        if (this.article._links['wp:featuredmedia']) {
            const mediaLink = this.article._links['wp:featuredmedia'][0].href;
            const response = await fetch(mediaLink);
            const media = await response.json();
            this.imageUrl = media.media_details.sizes.full.source_url;
        }

        const authorResponse = await fetch(`https://duclee-playground.fr/wp-json/wp/v2/users/${this.article.author}`);
        const author = await authorResponse.json();
        this.authorName = author.name;
    }
}
</script>

<style scoped>

</style>