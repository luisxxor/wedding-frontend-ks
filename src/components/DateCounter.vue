<template>
    <div class="date-counter-container">
        <div class="date-container">
            <span class="dayName text-center">
                <span class="dateComponent-text">
                    Viernes
                </span>
            </span>
            <span class="day text-center">
                26
            </span>
            <span class="month text-center">
                <span class="dateComponent-text">
                    Abril
                </span>
            </span>
            <span class="year text-center">2024</span>
        </div>
        <div class="counter-container">
            <div class="daysCounterContainer box-container">
                <img :src="dayContainer" alt="Day container" />
                <span class="quantity">{{ days }}</span>
                <span class="label">Días</span>
            </div>
            <div class="hourCounterContainer box-container">
                <img :src="hourContainer" alt="Hour container" />
                <span class="quantity">{{ hours }}</span>
                <span class="label">Horas</span>
            </div>
            <div class="minuteCounterContainer box-container">
                <img :src="minuteContainer" alt="Minute container" />
                <span class="quantity">{{ minutes }}</span>
                <span class="label">Min</span>
            </div>
            <div class="secondCounterContainer box-container">
                <img :src="secondContainer" alt="Second container" />
                <span class="quantity">{{ seconds }}</span>
                <span class="label">Seg</span>
            </div>
        </div>
    </div>
</template>

<style>
.date-counter-container {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 200px;
    margin-bottom: 4rem;
}

.date-container {
  padding: 0 3.5rem;
  display: grid;
  grid-template-columns: 1fr 4rem 1fr; /* defines 3 columns, with the 2nd column slightly wider than the others */
  grid-template-rows: auto 1fr; /* defines 2 rows, with the 2nd row taking up remaining space */
  grid-column-gap: 10px;
}

.dayName {
  grid-column: 1 / 2; /* place in column 1 */
  grid-row: 1 / 2; /* place in row 1 */
  display: flex;
  justify-content: center;
  align-items: center;
  letter-spacing: 2px;
}

.day {
  grid-column: 2 / 3; /* place in column 2 */
  grid-row: 1 / 2; /* place in row 1 */
  background: rgb(126,77,34);
  background: linear-gradient(0deg, rgba(126,77,34,1) 7%, rgba(205,158,50,1) 31%, rgba(247,242,142,1) 53%, rgba(229,209,110,1) 61%, rgba(208,167,70,1) 71%, rgba(200,152,55,1) 77%, rgba(124,80,33,1) 97%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  filter: drop-shadow(2px 3px 3px rgb(0 0 0 / 0.9));
  font-size: 4em;
  font-family: 'Alkatra', cursive;
}

.month {
  grid-column: 3 / 4; /* place in column 3 */
  grid-row: 1 / 2; /* place in row 1 */
  display: flex;
  align-items: center;
  letter-spacing: 2px;
}

.year {
  grid-column: 1 / 4; /* span all 3 columns */
  grid-row: 2 / 3; /* place in row 2 */
  font-family: 'Roboto', sans-serif;
  font-size: 1.2rem;
  letter-spacing: 2px;
}

.counter-container {
    display: flex;
    justify-content: space-between;
    gap: 1rem;
    height: 80px;
}

.box-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    flex: 1 1 0;
    position: relative;
}

.box-container > img {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}

.minuteCounterContainer {
    color: #fff;
}

.dateComponent-text {
  border-top: 2px solid #c99e67;
  border-bottom: 2px solid #c99e67;
  text-transform: uppercase;
  font-weight: 500;
  width: 100%;
  text-align: center;
}

.quantity {
    font-family: 'Alkatra', cursive;
    font-size: 1.5em;
}

.label {
    font-family: 'Roboto', sans-serif;
    font-size: 0.7em;
    text-transform: uppercase;
    letter-spacing: 2px;
}

@media (min-width:768px){
    .counter-container {
        height: 100px;
    }

    .dateComponent-text {
        font-size: 18px;
    }
    
    .year {
        font-size: 20px;
        margin-top: 0.6rem;
    }

    .date-container {
        padding: 0 3.5rem;
        grid-template-columns: 1fr 8rem 1fr;
        grid-template-rows: auto 1fr;
        grid-column-gap: 10px;
    }

    .date-counter-container {
        row-gap: 1rem;
        height: 261px;
        padding: 1rem 2rem;
    }
}
</style>

<script lang="ts" setup>
import { computed, ref } from 'vue';
import { format, differenceInDays, differenceInHours, differenceInMinutes, differenceInSeconds } from 'date-fns';
import { defineProps } from 'vue';
import dayContainer from '@/assets/svg/dayContainer.svg';
import hourContainer from '@/assets/svg/hourContainer.svg';
import minuteContainer from '@/assets/svg/minuteContainer.svg';
import secondContainer from '@/assets/svg/secondContainer.svg';

// Define prop screenHeight
defineProps<{ statusBarHeight: number }>();

const date = ref(new Date(2024, 3, 26, 18, 0, 0));
const currentDate = ref(new Date());

const dayName = computed(() => format(date.value, 'EEEE'));
const day = computed(() => format(date.value, 'd'));
const month = computed(() => format(date.value, 'MMMM'));
const year = computed(() => format(date.value, 'yyyy'));

const days = computed(() => differenceInDays(date.value, currentDate.value));

// Get the difference in hours but exclude the days
const hours = computed(() => differenceInHours(date.value, currentDate.value) % 24);

// Get the difference in minutes but exclude the hours and days
const minutes = computed(() => differenceInMinutes(date.value, currentDate.value) % 60);

// Get the difference in seconds but exclude the minutes, hours and days
const seconds = computed(() => differenceInSeconds(date.value, currentDate.value) % 60);

setInterval(() => {
    currentDate.value = new Date();
}, 1000);
</script>