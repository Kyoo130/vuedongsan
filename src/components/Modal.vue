<template>
  <div class="black-bg" v-if="modalOpen === true">
    <div class="white-bg">
      <h3>{{ oneRooms[clickInfo].title }}</h3>
      <img class="room-img" :src="oneRooms[clickInfo].image" :alt="oneRooms[clickInfo].title">
      <p>{{ oneRooms[clickInfo].count }}</p>
      <input type="number" v-model="month">
      <p>{{ month }}개월 선택 시 : {{ oneRooms[clickInfo].price * month }} 원</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MoDal',
  props: {
    oneRooms: Array,
    clickInfo: Number,
    modalOpen: Boolean,
  },
  data() {
    return {
      month: 1,
    }
  },
  watch: {
    month(a){
      if (a >= 13) {
        alert('1 ~ 12개월 까지만 입력이 가능합니다.')
      }
    }
  },
  components: {},
}
</script>

<style>
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