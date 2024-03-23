<template>
    <div class="footer-container" :style="{
        '--floral-footer': `url(${floralFooter})`,
    }">
        <div class="card">
            <div class="title">
                Confirma tu asistencia
            </div>
            <div class="text">
                ¡Queremos contar contigo en nuestra boda! Por favor, confirmanos tu asistencia vía WhatsApp.
            </div>
            <div class="contacts">
                <div class="contact">
                    <div class="contact-name">
                        Luis
                    </div>
                    <a class="contact-button" :href="contactUrlLuis">
                        Enviar mensaje
                    </a>
                </div>
                <div class="space-divider">
                    <!-- whatsapp icon -->
                    <img :src="whatsappIcon" alt="whatsapp icon" class="whatsapp-icon" />
                </div>
                <div class="contact">
                    <div class="contact-name">
                        Mariana
                    </div>
                    <a class="contact-button" :href="contactUrlMariana">
                        Enviar mensaje
                    </a>
                </div>
            </div>
        </div>
    </div>
</template>

<script lang="ts" setup>
    import whatsappIcon from '@/assets/svg/whatsapp-icon.svg';
    import floralFooter from '@/assets/floral-footer.webp';
 
    const contactUrlLuis = `https://api.whatsapp.com/send?phone=584242350991&text=Hola%20Luis!%20confirmo%20mi%20asistencia%20a%20la%20boda%20%F0%9F%98%8A`
    const contactUrlMariana = `https://api.whatsapp.com/send?phone=51946448464&text=Hola%20Mariana!%20confirmo%20mi%20asistencia%20a%20la%20boda%20%F0%9F%98%8A`
</script>

<style scoped>

.footer-container {
    position: relative;
}
.card {
    border-radius: 4px;
    background-color: #fff;
    position: relative;
    box-shadow: 0px 2px 1px -1px rgba(0, 0, 0, 0.2), 0px 1px 1px 0px rgba(0, 0, 0, 0.14), 0px 1px 3px 0px rgba(0, 0, 0, 0.12);
    padding: 1em;
    margin-top: 8rem;
    display: flex;
    justify-content: center;
    flex-direction: column;
    text-align: center;
    z-index: 2;
}

.contacts {
    display: flex;
    justify-content: space-between;
    margin-top: 1em;
}

.space-divider {
    border-right: 1px solid #000;
    position: relative;
}

.space-divider > img {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

.contact {
    display: flex;
    flex-direction: column;
}

.contact-name {
    font-family: 'Great Vibes', cursive;
    font-size: 2rem;
}

.contact-button {
    margin-top: .1rem;
    text-decoration: none;
    color: white;
    background-color: #023378;
    padding: .5rem 1rem;
    border-radius: 1rem;
    font-family: 'Roboto', sans-serif;
    font-weight: 500;
    text-transform: uppercase;
    font-size: .8rem;
}

.footer-container::before {
    content: '';
    position: absolute;
    background-image: var(--floral-footer);
    clip-path: polygon(0 0, 100% 0, 100% 50%, 0 50%);
    height: -webkit-fill-available;
    width: 100%;
    top: -83px;
    z-index: 1;
    background-repeat: no-repeat;
    background-size: cover;
    overflow: hidden;
}

.footer-container::after {
    content: '';
    position: absolute;
    background-image: var(--floral-footer);
    clip-path: polygon(0 54%, 100% 54%, 100% 100%, 0 100%);
    height: -webkit-fill-available;
    width: 100%;
    bottom: -81px;
    z-index: 1;
    background-repeat: no-repeat;
    background-size: cover;
    background-position: bottom;
}

.title {
    font-family: 'Great Vibes', cursive;
    font-size: 2rem;
}

.text { 
    font-family: 'Roboto', sans-serif;
    font-size: .8rem;
    letter-spacing: 2px;
}

.whatsapp-icon {
    height: 24px;
    width: 24px;
}

@media (min-width: 500px) {
    .footer-container {
        margin-top: 10rem;
        margin-bottom: 8em;
    }

    .footer-container::before {
        top: -120px;
    }
    .footer-container::after {
        bottom: -118px;
    }
}

@media (min-width: 650px) {
    .footer-container {
        margin-top: 12rem;
        margin-bottom: 10em;
    }

    .footer-container::before {
        top: -157px;
    }
    .footer-container::after {
        bottom: -155px;
    }
}

@media (min-width: 768px) {
    .title, .contact-name {
        font-size: 2.5rem;
    }

    .text {
        font-size: 1rem;
    }

    .contacts {
        justify-content: space-evenly;
    }

    .contact-button {
        font-size: 1rem;
    }

    .whatsapp-icon {
        height: 36px;
        width: 36px;
    }

    .footer-container {
        margin-top: 16em;
        margin-bottom: 14em;
    }

    .footer-container::before {
        top: -183px;
    }
    .footer-container::after {
        bottom: -179px;
    }
}
</style>
