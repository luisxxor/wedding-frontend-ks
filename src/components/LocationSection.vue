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

        <div class="invitations-container">
            <div class="invitations-icon-container">
                <img :src="invitations" alt="Invitaciones" />
            </div>

            <div class="invitations-title">
                {{ invitationsTitle }}
            </div>
            <div class="invitations-text">
                <ul>
                    <li v-for="guest in guests" :key="guest">
                        {{ guest }}
                    </li>
                </ul>
            </div>
        </div>

        <div class="dressing-container">
            <div class="dressing-icon-container">
                <img :src="dressingIcon" alt="Vestimenta" />
            </div>
            <div class="dressing-title">
                Vestimenta
            </div>
            <div class="dressing-text">
                Formal / Semi-Formal
            </div>
        </div>

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
    import partyIcon from '@/assets/svg/party-icon.svg';
    import dressingIcon from '@/assets/svg/dressing-icon.svg';
    import leaves1 from '@/assets/svg/leaves-1.svg';
    import leaves2 from '@/assets/svg/leaves-2.svg';
    import leaves3 from '@/assets/svg/leaves-3.svg';
    import hoops1 from '@/assets/svg/hoops-1.svg';
    import hoops2 from '@/assets/svg/hoops-2.svg';
    import hoops3 from '@/assets/svg/hoops-3.svg';
    import invitations from '@/assets/svg/invitations.svg';
    import { defineProps, computed } from 'vue';

    const locations = [
        {
            locationIcon: churchIcon,
            locationTime: 'de 12:30pm a 2:00pm',
            locationEventName: 'Ceremonia',
            locationName: 'Iglesia Evangélica Libre Ebenezer',
            locationMap: 'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d256.7544017574819!2d-67.33615267359657!3d10.228815917053296!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x8c2a9e7c3731c853%3A0x11f1f0db5d1b5939!2sIglesia%20Evang%C3%A9lica%20Libre%20Ebenezer!5e0!3m2!1ses-419!2sve!4v1680963468029!5m2!1ses-419!2sve'
        },
        {
            locationIcon: partyIcon,
            locationTime: 'desde las 2:00pm',
            locationEventName: 'Salón',
            locationName: 'Salón de Fiestas Zamora Eventos',
            locationMap: 'https://www.google.com/maps/embed?pb=!1m14!1m8!1m3!1d490.80291053790995!2d-67.3246683!3d10.2274044!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x8c2a9f8b904bed63%3A0x4ea5e795c8929c23!2sZamora%20Eventos%2C%20La%20Victoria!5e0!3m2!1ses-419!2sve!4v1680962511441!5m2!1ses-419!2sve'
        }
    ]

    const props = defineProps<{
        familyName: string,
        guests: string[],
    }>();

    const invitationsTitle = computed(() => props.familyName ? props.familyName : 'Invitados');
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

    .dressing-container, .invitations-container {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        z-index: 2;
    }

    .invitations-container {
        margin-bottom: 3em;
    }

    .invitations-icon-container {
        margin-left: 0.7em;
    }

    .dressing-icon-container > img, .invitations-icon-container > img {
        height: 50px;
    }

    .dressing-title, .invitations-title {
        font-family: 'Great Vibes', cursive;
        font-size: 2rem;
        line-height: .5;
    }

    .invitations-title {
        line-height: 1.2;
        text-align: center;
        margin-top: 0.6rem;
    }

    .invitations-text {
        margin-top: 0.6rem;
        font-family: 'Roboto', sans-serif;
        font-weight: 300;
        letter-spacing: 2px;
        width: 100%;
        text-align: center;
        border: 4px #d7aa41;
        border-style: double;
        padding: 0.6rem 0;
    }

    .invitations-text > ul {
        margin: 0;
        padding: 0;
        list-style: none;
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
        .dressing-title, .invitations-title {
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

        .invitations-icon-container > img {
            height: 70px;
        }

        .dressing-icon-container > img {
            height: 90px;
        }

        .dressing-container {
            margin-bottom: 3em;
        }


        .invitations-text {
            font-size: 1.2rem;
            line-height: 2rem;
            letter-spacing: 3px;
            width: 608px;
        }
    }


</style>