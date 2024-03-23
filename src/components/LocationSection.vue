<template>
    <div class="location-container">
        <Location
            v-for="location in locations"
            :key="location.locationName"
            :locationIcon="location.locationIcon"
            :locationTime="location.locationTime"
            :locationEventName="location.locationEventName"
            :locationName="location.locationName"
            :locationMap="location.locationMap"
        />

        <img :src="leaves1" id="leaves1">
        <img :src="leaves2" id="leaves2">
        <img :src="leaves3" id="leaves3">

        <div id="hoops-container-1">
            <img :src="hoops1" id="hoops1">
        </div>

        <div id="hoops-container-2">
            <img :src="hoops2" id="hoops2">
        </div>

        <div id="hoops-container-3">
            <img :src="hoops3" id="hoops3">
        </div>
    </div>
</template>

<script lang="ts" setup>
    import Location from './Location.vue';
    import churchIcon from '@/assets/svg/church-icon.svg';
    import leaves1 from '@/assets/svg/leaves-1.svg';
    import leaves2 from '@/assets/svg/leaves-2.svg';
    import leaves3 from '@/assets/svg/leaves-3.svg';
    import hoops1 from '@/assets/svg/hoops-1.svg';
    import hoops2 from '@/assets/svg/hoops-2.svg';
    import hoops3 from '@/assets/svg/hoops-3.svg';

    const locations = [
        {
            locationIcon: churchIcon,
            locationTime: 'desde las 6:00 pm',
            locationEventName: 'Ceremonia',
            locationName: 'Y\'s Recepciones & Eventos',
            locationMap: 'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d554.1693044361705!2d-77.06173103968294!3d-12.002002592819382!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x9105cfdefeb01b3b%3A0x4b6ecee14197402d!2sY&#39;s%20Recepciones%20%26%20Eventos!5e0!3m2!1ses-419!2spe!4v1711221529183!5m2!1ses-419!2spe'
        }
    ]
</script>

<style>
    .location-container {
        border-radius: 4px;
        background-color: #fff;
        position: relative;
        box-shadow: 1px -6px 27px 18px rgba(149,207,245,0.9);
        padding: 2rem;
        overflow: hidden;
    }

    .location-container > .location-item-container {
        margin-bottom: 6rem;
    }

    .location-item-container {
        z-index: 2;
    }

    .dressing-container {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        z-index: 2;
    }

    .dressing-icon-container > img {
        height: 50px;
    }

    .dressing-title {
        font-family: 'Great Vibes', cursive;
        font-size: 2rem;
        line-height: .5;
    }


    .dressing-text {
        font-family: 'Roboto', sans-serif;
        letter-spacing: 2px;
        font-weight: 300;
    }

    #leaves1 {
        position: absolute;
        top: 0;
        left: 0;
        width: 82px;
    }

    #leaves2 {
        position: absolute;
        width: 80px;
        top: 550px;
        right: -10px;
    }

    #leaves3 {
        position: absolute;
        width: 80px;
        bottom: -35px;
        left: -35px;
    }

    #hoops-container-1 {
        position: absolute;
        top: -36px;
        right: -36px;
        width: 452px;
        clip-path: polygon(50% 0, 100% 0, 100% 50%, 50% 50%);
    }

    #hoops-container-2 {
        position: absolute;
        height: 500px;
        top: 169px;
        left: -464px;
        width: 500px;
        z-index: 1;
    }
    
    #hoops-container-3 {    
        position: absolute;
        bottom: -20px;
        right: -34px;
        width: 500px;
        z-index: 1;
        clip-path: polygon(50% 50%, 100% 50%, 100% 100%, 50% 100%);
    }

    @media (min-width: 768px) {
        .dressing-title {
            font-size: 2.5rem;
        }

        .dressing-title {
            margin-top: 1.2rem;
        }

        .dressing-text {
            font-size: 1.2rem;
            margin-top: .8rem;
            letter-spacing: 3px;
        }

        .dressing-icon-container > img {
            height: 90px;
        }

        .dressing-container {
            margin-bottom: 3em;
        }
    }


</style>