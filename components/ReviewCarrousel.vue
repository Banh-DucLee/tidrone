<template>
    <section v-if="reviews.length > 0" class="review-section">
        <h2 class="title-2 text-center">Vos Retours</h2>
        <div class="reviews-carrousel" @mouseenter="stopAutoScroll" @mouseleave="startAutoScroll">
            <div class="reviews-container" :style="{transform: `translateX(-${currentIndex * 100}%)`}">
                <div class="review" v-for="(review, index) in reviews" :key="index">
                    <div class="review-content">
                        <p class="paragraph-regular">{{ review.comment }}</p>
                        <span class="review-divider"></span>
                    </div>
                    <p class="paragraph-bold review-author">{{ review.author }}, {{ review.jobTitle }} chez {{ review.company }}</p>
                </div>
            </div>
            <button class="review-button button-prev" :disabled="currentIndex === 0" @click="prevReview">
                <svg width="23" height="87" viewBox="0 0 23 87" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M0 43.5L22.5 0.19873L22.5 86.8013L0 43.5Z" fill="currentColor"/>
                </svg>                
            </button>
            <button class="review-button button-next" :disabled="currentIndex === reviews.length - 1" @click="nextReview">
                <svg width="23" height="87" viewBox="0 0 23 87" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M23 43.5L0.5 86.8013L0.5 0.19873L23 43.5Z" fill="currentColor"/>
                </svg>
            </button>
            <div class="review-indicators">
                <div class="indicator" v-for="(review, index) in reviews" :key="index" :class="{'active': index === currentIndex}" @click="goToReview(index)"></div>
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
            autoScrollInterval: null
        };
    },
    mounted() {
        this.startAutoScroll();
    },
    beforeDestroy() {
        this.stopAutoScroll();
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
        },
        startAutoScroll() {
            this.autoScrollInterval = setInterval(() => {
                if (this.currentIndex < this.reviews.length - 1) {
                    this.currentIndex++;
                } else {
                    this.currentIndex = 0;
                }
            }, 5000);
        },
        stopAutoScroll() {
            clearInterval(this.autoScrollInterval);
            this.autoScrollInterval = null;
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
        padding: 10% 15%;
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

    .review-content {
        position: relative;
    }

    .review-divider {
        position: absolute;
        top: 0;
        left: -15px;
        width: 3px;
        height: 25%;
        min-height: 50px;
        background-color: var(--color-primary-500);
    }

    .review-button {
        opacity: 0;
        z-index: -10;
        top: 50%;
        position: absolute;
        transform: translateY(-50%);
        transition: opacity 0.3s ease-in-out;
        border: none;
        background-color: transparent;
    }

    .review-button path {
        fill: var(--color-opacity-black-50);
    }

    .review-button:hover path {
        fill: var(--color-opacity-black-70);
    }

    .review-button:active path {
        fill: var(--color-opacity-black-80);
    }

    .review-button:disabled {
        display: none;
    }

    .button-prev {
        left: 0;
    }

    .button-next {
        right: 0;
    }

    .reviews-carrousel:hover .review-button {
        opacity: 1;
        z-index: inherit;
    }

    .review-indicators {
        position: absolute;
        bottom: 0;
        left: 50%;
        transform: translateX(-50%);
        display: flex;
        flex-flow: row nowrap;
    }

    .indicator {
        width: 12px;
        height: 12px;
        border-radius: 50%;
        background-color: var(--color-opacity-black-50);
        margin: 10px 5px;
        cursor: pointer;
    }

    .indicator.active {
        background-color: var(--color-primary-500);
    }
</style>