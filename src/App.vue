<template>
  <div id="app">
    <h1 data-id="league">League Maps</h1>
    <h2>NOW</h2>
    <ListRotation v-bind:schedule="schedules.league[0]"/>
    <h2>NEXT</h2>
    <ListRotation v-bind:schedule="schedules.league[1]"/>
    <h2>LATER</h2>
    <ListRotation v-bind:schedule="schedules.league[2]"/>
    <p class="credit">Live data provided by <img src="src/assets/splatoon2ink.png" width="16" height="16" alt="" /> Splatoon2.ink.</p>
    <h1 data-id="ranked">Ranked Maps</h1>
    <h2>NOW</h2>
    <ListRotation v-bind:schedule="schedules.gachi[0]"/>
    <h2>NEXT</h2>
    <ListRotation v-bind:schedule="schedules.gachi[1]"/>
    <h2>LATER</h2>
    <ListRotation v-bind:schedule="schedules.gachi[2]"/>
    <p class="credit">Live data provided by <img src="src/assets/splatoon2ink.png" width="16" height="16" alt="" /> Splatoon2.ink.</p>
    <h1 data-id="turf">Turf Maps</h1>
    <h2>NOW</h2>
    <ListRotation v-bind:schedule="schedules.regular[0]"/>
    <h2>NEXT</h2>
    <ListRotation v-bind:schedule="schedules.regular[1]"/>
    <h2>LATER</h2>
    <ListRotation v-bind:schedule="schedules.regular[2]"/>
    <p class="credit">Live data provided by <img src="src/assets/splatoon2ink.png" width="16" height="16" alt="" /> Splatoon2.ink.</p>
  </div>
</template>

<script>
import axios from 'axios'
import ListRotation from './components/ListRotation.vue'

export default {
  name: 'app',
  components: { ListRotation },
  data () {
    return {
      schedules: null,
      msg: 'Welcome to Your Vue.js App'
    }
  },
  mounted () {
    axios
      // .get('mocks/schedules.json')
      .get('https://cors-anywhere.herokuapp.com/https://splatoon2.ink/data/schedules.json')
      .then(response => (this.schedules = response.data))
  }
}
</script>

<style lang="scss">
body {
  margin: 0;
  padding: 0;
}

#app {
  font-family: Calibre, Helvetica, Arial, sans-serif;
  font-size: 18px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 30px auto;
  max-width: 640px;
}

h1 {
  font-family: reklame-script, 'Reklame Script', Calibre, Helvetica, Arial, sans-serif;
  font-weight: bold;
  font-size: 64px;
  line-height: 1em;
}

h2 {
  font-weight: bold;
  color: purple;
  text-align: left;
  font-size: 36px;
  margin-left: 220px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

.credit {
  text-align: left;
  margin-left: 220px;
  margin-bottom: 5em;
}
</style>
