<template>
    <section v-if="reviews.length > 0" class="review-section">
        <h2 class="title-2 text-center">Vos Retours</h2>
        <div class="reviews-carrousel">
            <div class="reviews-container" :style="{transform: `translateX(-${currentIndex * 100}%)`}">
                <div class="review" v-for="(review, index) in reviews" :key="index" :class="{'active': index === currentIndex}">
                    <div class="review-content">
                        <p class="paragraph-regular">{{ review.comment }}</p>
                        <span class="review-divider"></span>
                    </div>
                    <p class="paragraph-bold review-author">{{ review.author }}, {{ review.jobTitle }} chez {{ review.company }}</p>
                </div>
            </div>
            <div class="review-navigation">
                <button class="review-navigation-button" :disabled="currentIndex === 0" @click="prevReview">Prev</button>
                <button class="review-navigation-button" :disabled="currentIndex === reviews.length - 1" @click="nextReview">Next</button>
            </div>
        </div>
    </section>
</template>

<script>
import reviews from 'assets/json/reviews.json';

export default {
    props: {
        reviews: {
            type: Array,
            default: () => reviews
        }
    },
    data() {
        return {
            currentIndex: 0,
        };
    },
    methods: {
        prevReview() {
            if (this.currentIndex > 0) {
                this.currentIndex--;
            }
        },
        nextReview() {
            if (this.currentIndex < this.reviews.length - 1) {
                this.currentIndex++;
            }
        },
        goToReview(index) {
            this.currentIndex = index;
        }
    }
}
</script>

<style scoped>
    .reviews-carrousel {
        position: relative;
        border: 3px solid var(--color-opacity-black-25);
        border-radius: 5px;
        margin: 16px 10%;
        box-sizing: border-box;
        overflow: hidden;
    }

    .reviews-container {
        transition: transform 0.5s ease-in-out;
        display: flex;
        flex-flow: row nowrap;
    }

    .review {
        padding: 10%;
        transition: transform 0.5s ease-in-out;
        flex-shrink: 0;
        width: 100%;
        box-sizing: border-box;
        display: flex;
        flex-flow: column nowrap;
        align-items: center;
        justify-content: center;
        gap: 32px;
    }

    .review-navigation {
        top: 50%;
        position: absolute;
    }
</style>