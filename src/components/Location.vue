<template>
    <div class="location-item-container">
        <div class="location-icon">
            <img :src="locationIcon" alt="Location icon" />
        </div>
        <div class="location-time">
            {{ locationTime }}
        </div>
        <div class="location-event-name">
            {{ locationName }}
        </div>

        <div class="location-map">
            <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d554.1693044361705!2d-77.06173103968294!3d-12.002002592819382!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x9105cfdefeb01b3b%3A0x4b6ecee14197402d!2sY&#39;s%20Recepciones%20%26%20Eventos!5e0!3m2!1ses-419!2spe!4v1711221529183!5m2!1ses-419!2spe" width="600" height="450" style="border:0;" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
        </div>
    </div>
</template>

<script setup lang="ts">
import { defineProps } from 'vue';

const props = defineProps<{
    locationIcon: string;
    locationTime: string;
    locationEventName: string;
    locationName: string;
    locationMap: string;
}>();
</script>

<style scoped>
    .location-icon > img {
        height: 50px;
    }
    .location-map {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .location-map {
        width: fit-content;
        border: 4px #d7aa41;
        border-style: double;
    }
    .location-map > iframe {
        width: 100%;
        height: 300px;
    }

    .location-item-container {
        display: flex;
        justify-content: center;
        text-align: center;
        flex-direction: column;
    }

    .location-time, .location-name {
        letter-spacing: 2px;
        font-family: 'Roboto', sans-serif;
        font-size: .8rem;
    }

    .location-name {
        margin-bottom: 1em;
    }

    .location-event-name {
        font-family: 'Great Vibes', cursive;
        font-size: 2rem;
        line-height: 2;
    }

    .location-item-container {
        justify-content: center;
        display: flex;
        align-items: center;
    }
    
    /* Width 600px and height 450px for md devices */
    @media (min-width: 768px) {
        .location-map > iframe {
            width: 600px;
            height: 450px;
        }

        .location-time, .location-name {
            font-size: 1.2rem;
            line-height: 2rem;
            letter-spacing: 3px;
        }

        .location-event-name {
            font-size: 2.5rem;
        }
        .location-icon > img {
            height: 90px;
        }
    }

</style>