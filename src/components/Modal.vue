<template>
  <div class="black-bg" v-if="modalOpen === true">
    <div class="white-bg">
      <DisCount/>
      <!--      <button @click="modalOpen = false">닫기</button>-->
    </div>
  </div>
</template>

<script>
import DisCount from "@/components/DisCount";

export default {
  name: 'MoDal',
  props: {
    oneRooms: Array,
    clickInfo: Number,
    modalOpen: Boolean,
  },
  data() {
    return {}
  },
  components: {DisCount},
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