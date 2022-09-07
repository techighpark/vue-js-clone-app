<template lang="">
  <div>
    <h4 @click="emitOpenFn">{{ item.title }}</h4>
    <img :src="item.image" alt="" />
    <p>{{ item.content }}</p>
    <div>{{ item.price.toLocaleString() }}</div>
    <!-- <div>Total reported : {{ item.count }}</div>
    <button @click="increase(i)">Report</button> -->
    <hr />
  </div>
</template>
<script>
export default {
  name: 'Card',
  props: {
    item: Object,
    // increase: Function,
  },
  methods: {
    emitOpenFn() {
      this.$emit('openModal', this.item.id);
    },
  },
};
</script>
<style lang=""></style>
