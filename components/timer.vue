<template>
<!-- A timer with two buttons and tooltips explaining them -->
<div class="grid__timer">
          <article class="timer">
          <h3 class="timer__header">Baker's Timer</h3>
          <p class="timer__numbers">{{ minutes }}:{{ String(seconds).padStart(2, "0") }}</p>
          <div class="timer__button-container">
            <button type="button" class="timer__s-button"  data-toggle="tooltip" data-placement="top" title="Click here to start the 30min timer" @click="startTimer" v-if="!timerStarted">Start Timer</button>

            <button type="button" class="timer__s-button"  data-toggle="tooltip" data-placement="top" title="Click here to stop the 30min timer" @click="stopTimer" v-else>Stop Timer</button>

            <button type="button" class="timer__a-button" @click="toggle" data-toggle="tooltip" data-placement="bottom" title="Click here to adjust timer intervals">Adjust Time</button>

            <div class="timer__hide-wrap" v-if="!show">
              <input id="timer-input" class="timer__adjust" placeholder="Set timer length in minutes" v-model="minutes">
            </div>
          </div>
          </article>
        </div>
</template>

<script>
export default {
data () {
      return {
        // set values for the timer (will expand on later)
        minutes: 30,
        seconds: 0,
        counter: 0,
        intervalId: null,
        timerStarted: false,
        show: true,
      }
    },
    methods: {
      // a functions to start and stop the timer while changing button text
      startTimer() {
      if (!this.intervalId) {
        this.intervalId = setInterval(() => {
          if (this.seconds > 0) {
            this.seconds--
          } else if (this.minutes > 0) {
            this.minutes--
            this.seconds = 59
          } else {
            this.resetTimer()
            alert("Fold your dough!")
            this.counter++;
          }
        }, 1000)
      }
      this.timerStarted = !this.timerStarted;
    },
    stopTimer() {
      clearInterval(this.intervalId)
      this.intervalId = null;
      this.timerStarted = false;
    },
    toggle() {
        this.show = !this.show;
    }
    }
}
</script>