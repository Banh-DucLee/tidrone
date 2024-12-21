<template>
    <NuxtLink :to="`/article/${article.slug}`" class="shadow-base news-preview-container">
        <article class="news-wrapper">
            <div class="news-image-wrapper">
                <img class="news-image" :src="imageUrl" :alt="'Article sur ' + article.title" />
                <span class="news-image-mask"></span>
                <span class="button link-typo">Lire plus</span>
                <span class="divider"></span>
            </div>
            <div class="news-content">
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
            return new Date(rawDate).toLocaleDateString('fr-FR', {
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

        const authorResponse = await fetch(`https://cms.duclee-playground.fr/wp-json/wp/v2/users/${this.article.author}`);
        const author = await authorResponse.json();
        this.authorName = author.name;
    }
}
</script>

<style scoped>
    .news-preview-container {
        flex: 1;
        text-decoration: none;
        color: var(--color-main-black);
        border-radius: 5px;
        overflow: hidden;
    }

    .news-preview-container:hover {
        scale: 1.015;
    }

    .news-preview-container:hover .divider {
        height: 10px;
    }

    .news-preview-container:hover .news-image-mask:after {
        opacity: 0;
    }

    .news-preview-container:hover .button {
        transform: translateY(-5px);
    }

    .news-wrapper {
        position: relative;
        width: 100%;
        height: 100%;
        display: flex;
        flex-flow: column nowrap;
        justify-content: center;
    }

    .news-image-wrapper {
        position: relative;
        height: auto;
        width: 100%;
        aspect-ratio: 1.9;
    }

    .news-image {
        width: 100%;
        height: auto;
        object-fit: cover;
        aspect-ratio: 1.9;
    }

    .news-image-mask {
        content: '';
        display: block;
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: radial-gradient(var(--color-opacity-black-10), var(--color-opacity-black-50));
    }

    .news-image-mask:after {
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

    .button {
        display: block;
        position: absolute;
        bottom: 5px;
        left: 1px;
        padding: 8px 16px;
        border: 1px solid var(--color-main-black);
        background-color: var(--color-main-white);
        transition: transform 0.3s ease-in-out;
    }

    .news-content {
        flex: 1;
        padding: 8px;
        display: flex;
        flex-flow: column nowrap;
        gap: 16px;
        background-color: var(--color-opacity-black-10);
    }
</style>