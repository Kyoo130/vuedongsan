<template>
  <div>
    <img class="room-img" :src="oneRoom.image" alt="img">
    <h4 @click="send">{{ oneRoom.title }}</h4>
    <p>{{ oneRoom.price }} 원</p>
  </div>
</template>

<script>
export default {
  name: `Card`,
  props: {
    oneRoom: Object,
  },
  methods : {
    send(){
      this.$emit('openModal', this.oneRoom.id)
    }
  }
}
</script>

<style>
.room-img {
  max-width: 480px;
  margin-top: 40px;
}
</style>