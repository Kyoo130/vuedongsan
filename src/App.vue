<template>
  <div id="app">
    <!--    <h1>JSON DIFF</h1>-->

    <div class="black-bg" v-if="modal === true">
      <div class="white-bg">
        <h3>{{ oneRoomData[clickInfo].title }}</h3>
        <img class="room-img" :src="oneRoomData[clickInfo].image" :alt="oneRoomData[clickInfo].title">
        <p>{{ oneRoomData[clickInfo].content }}</p>
        <p>{{ oneRoomData[clickInfo].price }}</p>
        <button @click="modal = false">닫기</button>
      </div>
    </div>

    <div class="menu">
      <a v-for="(item, idx) in menu" :key="idx">{{ item }}</a>
    </div>

    <div v-for="(item, i) in oneRoomData" :key="i">
      <img class="room-img" :src="item.image" alt="img">
      <h3 @click="modal = true; clickInfo = i">{{ item.title }}</h3>
      <p>{{ item.price }}</p>
    </div>

  </div>
</template>

<script>
import {oneRoom} from "@/assets/oneRoom";

export default {
  name: 'App',
  data() {
    return {
      clickInfo: 0,
      oneRoomData: oneRoom,
      modal: false,
      menu: ['Home', 'Shop', 'About'],
    }
  },
  methods: {
    increase() {
      this.report += 1;
    }
  },
  components: {}
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

.room-img {
  max-width: 480px;
  margin-top: 40px;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  max-width: 1048px;
  margin: 0 auto;
  background: #fff;
  border-radius: 8px;
  padding: 20px;
}

</style>