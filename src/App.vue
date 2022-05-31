<template>
  <div id="app">
    <MoDal :oneRooms="oneRooms" :clickInfo="clickInfo" :modalOpen="modalOpen"/>

    <div class="menu">
      <a v-for="(item, idx) in menu" :key="idx">{{ item }}</a>
    </div>

    <Card @openModal="modalInfo = true; clickInfo = $event" :oneRoom="oneRooms[i]" v-for="(item, i) in oneRooms"
          :key="i"/>
  </div>
</template>

<script>
import oneRoomData from "@/assets/oneRoom";
import MoDal from "@/components/Modal";
import Card from "@/components/Card";

export default {
  name: 'App',
  data() {
    return {
      oneRooms: oneRoomData,
      clickInfo: 0,
      modalInfo: false,
      menu: ['Home', 'Shop', 'About'],
    }
  },
  methods: {
    increase() {
      this.report += 1;
    }
  },
  components: {Card, MoDal}
}
</script>

<style>
body {
  padding: 0;
  margin: 0;
}

*, *::before, *::after {
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 0 0 5px 5px;
}

.menu a {
  color: #fff;
  padding: 10px;
  text-decoration: none;
  font-weight: bold;
}

</style>