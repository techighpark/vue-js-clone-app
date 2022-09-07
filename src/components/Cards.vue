<template lang="">
  <div v-for="(item, i) in importProducts" :key="i">
    <div @click="openModal(i)">
      <img :src="item.image" class="room-img" />
      <h4>{{ item.title }}</h4>
      <div>{{ item.content }}</div>
      <div>{{ item.price.toLocaleString() }}</div>
    </div>
    <div>Reported : {{ item.count }}</div>
    <button @click="increase(i)">Report</button>
  </div>
</template>
<script>
export default {
  name: 'Cards',
  props: {
    importProducts: Array,
    increase: Function,
    openModal: Function,
  },
};
</script>
<style lang=""></style>
