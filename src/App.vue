<template>
  <v-app>
    <v-app-bar
      app
      style="background-color: #2c3e50"
      dark
    >
      <v-spacer />
      <v-toolbar-title class="white--text">
        <h1>Reykt Rjúpa 2020</h1>
      </v-toolbar-title>
      <v-spacer />
    </v-app-bar>

    <v-main style="background-color: #34495e">
      <v-row align="center" justify="center" style="margin: 50px 0px">
          <Timer/>
      </v-row>
      <v-row align="center" justify="center">
        <v-col align="center" justify="center">
            <Lads/>
        </v-col>
      </v-row>
      <v-row align="center" justify="center">
      </v-row>
    </v-main>
  </v-app>
</template>

<script>
import Lads from './components/Lads';
import Timer from './components/Timer';

export default {
  name: 'App',

  components: {
    Lads,
    Timer,
  },
  data() {
    return {
    }
  },
};
</script>

<style>
html, body{
  overflow-y: hidden;
}
</style>