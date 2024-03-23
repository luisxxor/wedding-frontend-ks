<script setup lang="ts">
import Cover from './components/Cover.vue';
import DateCounter from './components/DateCounter.vue';
import LocationSection from './components/LocationSection.vue';
import InvitationFooter from './components/InvitationFooter.vue';
import LastVerse from './components/LastVerse.vue';
import { ref, onMounted } from 'vue';
import axios from 'axios';
import type Guest from './types/guest';

const screenHeight = window.screen.height;
const visualViewportHeight = window.visualViewport?.height;
const screenWidth = window.screen.width;
const statusBarHeight = screenWidth < 768 ? screenHeight - (visualViewportHeight || 0) : 0;

let loadPage = ref(false);

const familyName = ref('');
const guestNames = ref<string[]>([]);

onMounted(async () => {
  setTimeout(() => {
    loadPage.value = true
  }, 2000);
});

</script>

<template>
  <div
    :class="
      loadPage ? 'animate__animated animate__fadeIn animate_slower'
      : ''"
  >
    <header v-show="loadPage">
      <Cover
        :statusBarHeight="statusBarHeight"
      />
    </header>
    <main v-show="loadPage">
      <DateCounter :statusBarHeight="statusBarHeight" />
      <LocationSection
        :family-name="familyName"
        :guests="guestNames"
      />
    </main>
    <footer v-show="loadPage">
      <InvitationFooter />
    </footer>
    <Transition name="shrink">
      <div class="loader" v-if="!loadPage">
        <div class="cloak"></div>
        <div class="lds-heart">
          <div></div>
        </div>
      </div>
    </Transition>
  </div>
</template>

<style>
.shrink-enter-active,
.shrink-leave-active {
  transition: 0.5s all ease;
}

.shrink-enter-from,
.shrink-leave-to {
  transform: scale(0);
}

.loader {
  position: absolute;
  z-index: 2000;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center
}

.lds-heart {
  display: inline-block;
  position: relative;
  width: 160px;
  height: 160px;
  transform: rotate(45deg);
  transform-origin: 80px 80px;
}
.lds-heart div {
  top: 64px;
  left: 64px;
  position: absolute;
  width: 64px;
  height: 64px;
  background: #A8415B;
  animation: lds-heart 1.2s infinite cubic-bezier(0.215, 0.61, 0.355, 1);
}
.lds-heart div:after,
.lds-heart div:before {
  content: " ";
  position: absolute;
  display: block;
  width: 64px;
  height: 64px;
  background: #A8415B;
}
.lds-heart div:before {
  left: -48px;
  border-radius: 50% 0 0 50%;
}
.lds-heart div:after {
  top: -48px;
  border-radius: 50% 50% 0 0;
}
@keyframes lds-heart {
  0% {
    transform: scale(0.95);
  }
  5% {
    transform: scale(1.1);
  }
  39% {
    transform: scale(0.85);
  }
  45% {
    transform: scale(1);
  }
  60% {
    transform: scale(0.95);
  }
  100% {
    transform: scale(0.9);
  }
}

</style>