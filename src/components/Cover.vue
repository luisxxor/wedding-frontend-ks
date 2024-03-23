<template>
    <div
        class="cover-container"
        :style="{
            height: height,
            backgroundImage: `url(${background})`
        }"
    >
        <div class="verse text-center animate__animated animate__fadeInDown animate__delay-1s animate__slow">
            El que no ama no ha conocido a Dios, porque Dios es amor.

            <span class="verse-ref">1 Juan 4:8</span>
        </div>

        <div class="floral-hoop-container animate__animated animate__zoomIn animate__delay-2s animate__slow">
            <img v-show="!floralHoopLoaded" class="floral-hoop" :src="floralHoopThumbnail" alt="Floral hoop">
            <img v-show="floralHoopLoaded" class="floral-hoop" :src="floralHoop" alt="Floral hoop" @load="floralHoopLoaded = true" />
        </div>

        <div class="footer text-center">
            <div class="footer-message animate__animated animate__bounceIn animate__delay-3s animate__slow">
                Tenemos el honor de invitarte a nuestra boda.
            </div>
            <div class="coverImageContainer animate__animated animate__flipInX animate__delay-4s animate__slow">
                <img
                    v-show="!coverImageLoaded"
                    class="coverImage"
                    :src="coverImageThumbnail"
                    alt="Cover image"
                >
                <img
                    v-show="coverImageLoaded"
                    class="coverImage"
                    :src="coverImage1024"
                    :srcset="`${coverImageSm} 330w, ${coverImage1024} 1024w`"
                    sizes="(max-width: 600px) 330px, (min-width: 601px) 100%, 1024px"
                    alt="Cover image"
                    @load="coverImageLoaded = true"
                >
                <div
                    id="coverImageBottom"
                    :style="{
                        background: `url(${coverImageBottom})`,
                        backgroundClip: 'content-box',
                    }"
                ></div>
            </div>
        </div>
    </div>
</template>

<script lang="ts" setup>
import coverImage1024 from '../assets/cover-image-1024.jpg';
import coverImageSm from '../assets/cover-image-sm.jpg';
import coverImageThumbnail from '../assets/cover-image-thumbnail.jpg';
import background400 from '../assets/background-400.png';
import background800 from '../assets/background-800.png';
import floralHoop from '../assets/floral-hoop.png';
import floralHoopThumbnail from '../assets/floral-hoop-thumbnail.png'
import coverImageBottom from '../assets/svg/cover-image-bottom.svg';
import { defineProps, computed, ref } from 'vue';

const props = defineProps<{
    statusBarHeight: number;
}>();

let floralHoopLoaded = ref(false);
let coverImageLoaded = ref(false);

// Get viewport width
const vw = computed(() => Math.max(document.documentElement.clientWidth || 0, window.innerWidth || 0));
let background: string|null = null;

if (vw.value < 600) {
    background = background400;
} else {
    background = background800;
}

const height = computed(() => (props.statusBarHeight && props.statusBarHeight > 0) ? 
    `calc(100vh + 3em - ${props.statusBarHeight}px)`
    : 'calc(100vh - 2em)'
);
</script>

<style scoped>

.floral-hoop-container {
    display: flex;
    justify-content: center;
    margin: 0 2.5rem 0 1.5rem;
}

.floral-hoop {
    width: 100%;
    max-width: 377px;
}

.cover-container {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    margin-bottom: 2em;
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
}

.verse {
    margin: 2rem 4rem 0 4rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    font-family: 'Alkatra', cursive;
    text-transform: uppercase;
    font-size: 12px;
}

.verse-ref {
    text-transform: none;
}

.coverImageContainer {
    position: relative;
}

.coverImage {
    max-width: 100%;
    height: auto;
    object-fit: cover;
    max-height: 150px;
    width: 100%;
}

#coverImageBottom {
    position: absolute;
    left: 0;
    bottom: 0;
    width: 100%;
    height: 20px;
}

.footer {
    display: flex;
    flex-direction: column;
}

.footer-message {
    font-family: 'Alkatra', cursive;
    margin: 0 2rem 1rem 2rem;
    text-transform: uppercase;
    font-size: 12px;
}

.coverImageContainer{
    overflow:hidden;
    position:relative;
}
.coverImageContainer::before{
    content:'';
    font-family:'shape divider from ShapeDividers.com';
    position: absolute;
    bottom: -1px;
    left: -1px;
    right: -1px;
    top: -5px;
    z-index: 3;
    pointer-events: none;
    background-repeat: no-repeat; 
    background-size: 112% 22px;
    background-position: 50% 0%;    
    background-image: url('data:image/svg+xml;charset=utf8, <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 35.28 2.17" preserveAspectRatio="none"><path d="M0 .5c3.07.55 9.27-.42 16.14 0 6.88.4 13.75.57 19.14-.11V0H0z" fill="%23ffffff"/><path d="M0 1c3.17.8 7.29-.38 10.04-.55 2.75-.17 9.25 1.47 12.67 1.3 3.43-.17 4.65-.84 7.05-.87 2.4-.02 5.52.88 5.52.88V0H0z" opacity=".5" fill="%23ffffff"/><path d="M0 1.85c2.56-.83 7.68-.3 11.79-.42 4.1-.12 6.86-.61 9.58-.28 2.73.33 5.61 1.17 8.61 1 3-.19 4.73-.82 5.3-.84V.1H0z" opacity=".5" fill="%23ffffff"/></svg>'); 
}

@media (min-width:768px){
    .coverImageContainer::before{
        background-size: 112% 32px;
        background-position: 50% 0%;   
    }

    .cover-container {
        height: fit-content!important;
    }

    .coverImage {
        max-height: 50vh;
    }

    .verse {
        font-size: 16px;
    }

    .verse-ref {
        font-size: 14px;
        margin-top: .4rem;
    }

    .footer-message {
        font-size: 16px;
    }
}
 
@media (min-width:1025px){
    .coverImageContainer::before{ 
        bottom: -0.1vw;
        left: -0.1vw;
        right: -0.1vw;
        top: -0.1vw; 
        background-size: 113% 40px;
        background-position: 50% 0%;  
    }
}

@media (min-width:2100px){
    .coverImageContainer::before{
        background-size: 113% calc(2vw + 40px);
    }
}
 

</style>
