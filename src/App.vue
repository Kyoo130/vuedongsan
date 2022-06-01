<template>
  <div id="app">
    <transition name="fade">
      <MoDal @closeModal="modalInfo = false" :oneRooms="oneRooms" :clickInfo="clickInfo" :modalOpen="modalInfo"/>
    </transition>

    <div class="menu">
      <a v-for="(item, idx) in menu" :key="idx">{{ item }}</a>
    </div>

    <DisCount/>

    <button @click="priceSort">정렬</button>
    <button @click="sortBack">되돌리기</button>

    <Card @openModal="modalInfo = true; clickInfo = $event" :oneRoom="oneRooms[i]" v-for="(item, i) in oneRooms"
          :key="i"/>
  </div>
</template>

<script>
import oneRoomData from "@/assets/oneRoom";
import MoDal from "@/components/Modal";
import Card from "@/components/Card";
import DisCount from "@/components/DisCount";

export default {
  name: 'App',
  data() {
    return {
      oneRoomsOrigin: [...oneRoomData],
      oneRooms: oneRoomData,
      clickInfo: 0,
      modalInfo: false,
      menu: ['Home', 'Shop', 'About'],
    }
  },
  methods: {
    increase() {
      this.report += 1;
    },
    priceSort() {
      this.oneRooms.sort(function (a, b) {
        return a.price - b.price
      })
    },
    sortBack() {
      this.oneRooms = [...this.oneRoomsOrigin]
    }
  },
  components: {DisCount, Card, MoDal}
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

.fade-enter-from {
  opacity: 0;
}

.fade-enter-active {
  transition: all 1s;
}

.fade-enter-to {
  opacity: 1;
}

</style>