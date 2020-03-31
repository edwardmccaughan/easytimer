<template>
  <div>
    <h1 v-if="seconds_remaining > 0">
      {{ Math.floor(seconds_remaining / 60) }} 
      :
      {{ seconds_remaining % 60 }}
    </h1>
    <h1 v-else>done!</h1>


    <div class="times">
      <button class="btn btn-primary btn-lg" v-on:click="seconds_remaining=3">
        3s
      </button>

      <button class="btn btn-primary btn-lg" v-on:click="seconds_remaining=30">
        30s
      </button>

      <button class="btn btn-primary btn-lg" v-on:click="seconds_remaining=60">
        1m
      </button>

      <button class="btn btn-primary btn-lg" v-on:click="seconds_remaining=180">
        3m
      </button>

      <button class="btn btn-primary btn-lg" v-on:click="seconds_remaining=240">
        4m
      </button>

      <button class="btn btn-primary btn-lg" v-on:click="seconds_remaining=300">
        5m
      </button>

      <button class="btn btn-primary btn-lg" v-on:click="seconds_remaining=600">
        10m
      </button>

      <button class="btn btn-primary btn-lg" v-on:click="seconds_remaining=900">
        15m
      </button>

      <button class="btn btn-primary btn-lg" v-on:click="seconds_remaining=1200">
        20m
      </button>

      <button class="btn btn-primary btn-lg" v-on:click="seconds_remaining=1500">
        25m
      </button>

      <button class="btn btn-primary btn-lg" v-on:click="seconds_remaining=1800">
        30m
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
      },
      update_time() {
        setTimeout(() => {
          console.log('counting down')
            if(this.seconds_remaining > 0) {
              this.seconds_remaining--;
            } else if (this.seconds_remaining == 0) {
              this.play_alert() 
              this.seconds_remaining--;
            }
            this.update_time()
          }, 1000);
      }
    },
    mounted() {
      this.update_time()
    },
    // watch: {
    //   seconds_remaining: {
    //     handler(value) {
    //       if (value > 0) {
    //         setTimeout(() => {
    //           this.seconds_remaining--;
    //         }, 1000);
    //       } else if (value == 0) {
    //         this.play_alert() 
    //       }
    //     },
    //     immediate: true // This ensures the watcher is triggered upon creation
    //   }
    // }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

h1 {
  font-size: 7.0em;
  color: white;
}

button {
  font-size: 2em;
  margin: 0.3em;
  padding: 0.2em 1.0em;
}
</style>
