<script>
export default {
    data() {
        return {
            timerList: [],
            timerId: 0,
        }
    },
    methods: {
        addNewTimer: function () {
            this.timerList.push({
                hour: '0' + 0,
                minuts: '0' + 0,
                seconds: '0' + 0,
                startTimer: '',
                showHours: false,
                showMin: false,
            })
        },
    }
}
</script>

<template>
    <div v-for="(item, index) in timerList" :key="index++">
        {{ item }}
        <div v-on:click="addNewTimer" class="timer timer-add">
            <h2 class="timer__plus">+</h2>
        </div>
    </div>
</template>

<style>
.timer-add {
    display: flex;
    justify-content: center;
    align-items: center;
}

.timer-add:hover {
    cursor: pointer;
}
</style>