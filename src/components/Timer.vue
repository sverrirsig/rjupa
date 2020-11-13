<template>
    <v-row>
        <v-col></v-col>
        <v-col v-for="times in times" :key="times.id" style="margin: 0px">
            <TimerCard v-bind:time="times" :key="times.id"></TimerCard>
        </v-col>
        <v-col></v-col>
    </v-row>
</template>

<script>
import TimerCard from './TimerCard';

export default {
    components: {
        TimerCard,
    },
  data() {
      return {
          startTime: "July 7, 2017 12:03:00",
            endTime: "November 20, 2020 16:00:00",
            times: [
                { id: 0, text: "Days", time: 1 },
            { id: 1, text: "Hours", time: 1 },
            { id: 2, text: "Minutes", time: 1 },
            { id: 3, text: "Seconds", time: 1 }
            ],
            progress: 100,
            // isActive: false,
            timeinterval: undefined
      }
  },
  methods: {
    updateTimer: function() {
      if (
        this.times[3].time > 0 ||
        this.times[2].time > 0 ||
        this.times[1].time > 0 ||
        this.times[0].time > 0
      ) {
        this.getTimeRemaining();
        this.updateProgressBar();
      } else {
        clearTimeout(this.timeinterval);
        // this.times[3].time = this.times[2].time = this.times[1].time = this.times[0].time = 0;
         this.progress = 0;
         this.times[0].time = "Roll it"
         this.times[0].text = ""
         this.times[1].time = "Light it"
         this.times[1].text = ""
         this.times[2].time = "Pass it"
         this.times[2].text = ""
         this.times[3].time = "Arooouund"
         this.times[3].text = ""
      }
    },
    getTimeRemaining: function() {
      let t = Date.parse(new Date(this.endTime)) - Date.parse(new Date());
     if(t >= 0){
      this.times[3].time = Math.floor(t / 1000 % 60); //seconds
      this.times[2].time = Math.floor(t / 1000 / 60 % 60); //minutes
      this.times[1].time = Math.floor(t / (1000 * 60 * 60) % 24); //hours
      this.times[0].time = Math.floor(t / (1000 * 60 * 60 * 24)); //days
       }else {
         this.times[3].time = this.times[2].time = this.times[1].time = this.times[0].time = 0;
         this.progress = 0;
       }
    },
    updateProgressBar: function() {
      let startTime = Date.parse(new Date(this.startTime));
      let currentTime = Date.parse(new Date());
      let endTime = Date.parse(new Date(this.endTime));
      let interval = parseFloat(
        (currentTime - startTime) / (endTime - startTime) * 100
      ).toFixed(2);
      this.progress = 100-interval;
    }
  },
  mounted() {
      this.updateTimer();
  },
  created: function() {
    this.updateTimer();
    this.timeinterval = setInterval(this.updateTimer, 1000);
  }
};


</script>