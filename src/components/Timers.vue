<script>
import Timer from './Timer.vue';

export default {
    data() {
        return {
            timerList: [],
        }
    },
    components: {
        Timer
    },
    methods: {
        addNewTimer: function () {
            this.timerList.push({
                hour: '0' + 0,
                minuts: '0' + 0,
                seconds: '0' + 0,
                startTimer: '',

                startBtn: function (evt) {
                    evt.target.closest('.timer')
                        .querySelector('.timer__time')
                        .classList
                        .add('timer__time_color_white');
                    evt.target.closest('.timer')
                        .querySelector('.timer__management-btn-reset')
                        .classList
                        .add('timer__management-btn-reset_color_white');
                    evt.target.closest('.timer')
                        .querySelector('.timer__management-btn-start')
                        .classList
                        .add('timer__management-btn-start_color_white');

                    evt.target
                        .classList
                        .toggle('timer__management-btn_view_paused');

                    const checkPaused = evt.target.classList.contains('timer__management-btn_view_paused');
                    const showMinutes = evt.target.closest('.timer').querySelector('.timer__time-min');
                    const showHour = evt.target.closest('.timer').querySelector('.timer__time-hour');

                    if (!checkPaused) {
                        evt.target.closest('.timer')
                            .querySelector('.timer__time')
                            .classList
                            .remove('timer__time_color_white');
                        return clearInterval(this.startTimer);
                    } this.startTimer = setInterval(() => {
                        this.seconds++;

                        this.seconds = this.seconds < 10 ? '0' + this.seconds : this.seconds;

                        if (this.seconds >= 60) {
                            this.minuts++;

                            this.minuts = this.minuts < 10 ? '0' + this.minuts : this.minuts;
                            this.seconds = '0' + 0;

                            this.showMin = true;
                            this.showMin && showMinutes.classList.remove('timer__time-invise-min');

                        }

                        if (this.minuts >= 60) {
                            this.hour++;

                            this.hour = this.hour < 10 ? '0' + this.hour : this.hour;
                            this.minuts = '0' + 0;

                            this.showHours = true;

                            this.showMin && showHour.classList.remove('timer__time-invise-hour');
                        }

                    }, 10)
                },
                stopBtn: function (evt) {
                    this.hour = '0' + 0;
                    this.minuts = '0' + 0;
                    this.seconds = '0' + 0;

                    this.showHours = false;
                    this.showMin = false;

                    evt.target.closest('.timer')
                        .querySelector('.timer__time')
                        .classList
                        .remove('timer__time_color_white');
                    evt.target.closest('.timer')
                        .querySelector('.timer__management-btn-reset')
                        .classList
                        .remove('timer__management-btn-reset_color_white');
                    evt.target.closest('.timer')
                        .querySelector('.timer__management-btn-start')
                        .classList
                        .remove('timer__management-btn-start_color_white');

                    const startBtn = evt.target.closest('.timer').querySelector('.timer__management-btn-start');
                    startBtn.classList.remove('timer__management-btn_view_paused');

                    const showMinutes = evt.target.closest('.timer').querySelector('.timer__time-min');
                    const showHour = evt.target.closest('.timer').querySelector('.timer__time-hour');
                    showMinutes.classList.add('timer__time-invise-min');
                    showHour.classList.add('timer__time-invise-hour');

                    return clearInterval(this.startTimer);
                },
            }
            )
        },
    },
}
</script>

<template>
    <section class="timers">
        <Timer v-for="(timer, index) in timerList" :key="index++" :timer_data="timer" />


        <div v-on:click="addNewTimer" class="timer timer-add">
            <h2 class="timer__plus">+</h2>
        </div>
    </section>
</template>

<style>
.timers {
    display: grid;
    grid-template-columns: repeat(3, 225px);
    grid-template-rows: repeat(auto-fit, 120px);
    justify-content: center;
    color: rgba(158, 158, 158, 1);
    gap: 45px 50px;
    padding: 72px 0;
}

.timer-add {
    display: flex;
    justify-content: center;
    align-items: center;
}

.timer-add:hover {
    cursor: pointer;
}

.timer-add:active {
    opacity: .8;
    color: rgba(255, 255, 255, 1);
}

.timer-add:active>.timer__plus {
    opacity: 1;
}

@media (max-width: 900px) {
    .timers {
        grid-template-columns: repeat(2, 225px);
        gap: 45px 50px;
    }
}

@media (max-width: 600px) {
    .timers {
        grid-template-columns: repeat(1, 225px);
    }
}
</style>