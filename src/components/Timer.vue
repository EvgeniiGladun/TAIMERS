<script>
export default {
  data() {
    return {}
  },
  props: {
    timer_data: {
      type: Object,
      default() {
        return {}
      },

    }
  },
}

</script>

<template>
  <div class="timer">
    <div class="timer__time">
      <div class="timer__time-hr timer__time-invise-hour">
        <span class="timer__time-figure timer__time-hour">{{ timer_data.hour }}</span>
        <span class="timer__time-colon">:</span>
      </div>

      <div class="timer__time-min timer__time-invise-min">
        <span class="timer__time-figure timer__time-minuts">{{ timer_data.minuts }}</span>
        <span class="timer__time-colon">:</span>
      </div>

      <span class="timer__time-figure timer__time-minuts">{{ timer_data.seconds }}</span>
    </div>
    <div class="timer__management">
      <div class="timer__management-container">
        <button v-on:click="timer_data.startBtn" class="timer__management-btn timer__management-btn-start"></button>
        <button v-on:click="timer_data.stopBtn" class="timer__management-btn timer__management-btn-reset"></button>
      </div>
    </div>
  </div>
</template>

<style>
.timer {
  width: 225px;
  height: 120px;
  background-color: rgba(105, 105, 105, 1);
}

.timer__time {
  display: flex;
  justify-content: center;
  align-items: center;
  border-bottom: solid 1px rgba(158, 158, 158, 1);
  height: 60px;
}

.timer__time_color_white {
  color: rgba(255, 255, 255, 1);
  border-color: rgba(255, 255, 255, 1);
}

.timer__time-invise-min,
.timer__time-invise-hour {
  display: none;
}

.timer__management {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 60px;
}

.timer__management-container {
  display: flex;
  justify-content: space-between;
  width: 100px;
}

.timer__management-btn {
  width: 20px;
  height: 20px;
  background-color: rgba(158, 158, 158, 1);
  border: none;
}

.timer__management-btn:hover {
  cursor: pointer;
}

.timer__management-btn:active {
  opacity: .8;
}

.timer__management-btn-start {
  width: 0;
  height: 0;
  background-color: rgba(105, 105, 105, 1);
  border-left: 17px solid rgba(158, 158, 158, 1);
  border-top: 10px solid transparent;
  border-bottom: 10px solid transparent;
}

.timer__management-btn_view_paused {
  width: 10px;
  height: 20px;
  border-color: rgba(255, 255, 255, 1);
  border-style: double;
  border-width: 0px 10px 0 0;
}

.timer__management-btn-start_color_white {
  border-left-color: rgba(255, 255, 255, 1);
}

.timer__management-btn-reset_color_white {
  background-color: rgba(255, 255, 255, 1);
}

.timer-add {
  display: flex;
  justify-content: center;
  align-items: center;
}

.timer-add:hover {
  cursor: pointer;
}
</style>