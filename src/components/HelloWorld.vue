<template>
  <div>
    <h1>{{ Math.floor(seconds_remaining / 60) }} : {{ seconds_remaining % 60 }}</h1>

    <div class="times">
      <button v-on:click="seconds_remaining=10">
        10s
      </button>

      <button v-on:click="seconds_remaining=30">
        30s
      </button>

      <button v-on:click="seconds_remaining=60">
        1m
      </button>

      <button v-on:click="seconds_remaining=180">
        3m
      </button>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'HelloWorld',
    data() {
      return {
        seconds_remaining: -1
      }
    },
    methods: {
      play_alert() {
        console.log('trying to play...')
        var audio = new Audio(require('./gong.mp3'))
        audio.play()
      }
    },

    watch: {
      seconds_remaining: {
        handler(value) {

          if (value > 0) {
            setTimeout(() => {
              this.seconds_remaining--;
            }, 1000);
          } else if (value == 0) {
            this.play_alert() 
          }
        },
        immediate: true // This ensures the watcher is triggered upon creation
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
