<template>
  <div>
    <v-img contain height="400px" width="400px" style="border-radius: 50%;" alt="Beautiful son of a bitch" :src="getImgUrl(lads[index].lad)"><v-img contain height="250px" width="250px" src="https://lh3.googleusercontent.com/proxy/mL0dxfq-sxOHBXouW5m39a30K9UxpdWIvJzo6GseqldlwVAYTnULjIEZSse_4K3Xvn3mwDeLJrQKN2SD7tV2aucCqWY7fMjPgXfG_9pqZ_vnaHQBDAWapwmwnH32" :style="lads[index].jointPosition"></v-img></v-img>
  </div>
</template>

<script>
export default {
  name: 'Lads',
  data() {
    return {
      index: 0,
      lads: [
        {
          lad: 'axel.jpg',
          jointPosition: "position: absolute;left: 25px;top: -8px;"
        },
        {
          lad: 'daniel.jpg',
          jointPosition: "position: absolute;left: 25px;top: 55px;"
        },
        {
          lad: 'frissi.jpg',
          jointPosition: "position: absolute;left: 30px;top: -18px;"
        },
        {
          lad: 'helgi.jpg',
          jointPosition: "position: absolute;left: -5px;top: 35px;"
        },
        {
          lad: 'leifur.jpg',
          jointPosition: "position: absolute;left: 13px;top: 46px;"
        },
        {
          lad: 'svessi.jpg',
          jointPosition: "position: absolute;left: 10px;top: 40px;"
        }]
    }
  },
  methods: {
    getImgUrl(pic) {
      return require('../assets/'+pic)
    },
    updateImage() {
      this.index = (this.index + 1) % this.lads.length;
    }
  },
  created() {
    setInterval(this.updateImage, 1000);
  }
}
</script>