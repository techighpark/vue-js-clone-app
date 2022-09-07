<template>
  <div class="discount">
    <h4>Discount Now for {{ amount }}%</h4>
  </div>
</template>
<script>
export default {
  name: 'Banner',
  data() {
    return {
      amount: 5,
    };
  },
  mounted() {
    setInterval(() => {
      if (this.amount > 0) {
        this.amount--;
      } else {
        this.amount = 10;
        clearInterval();
      }
    }, 1000);
  },
};
</script>
<style scoped>
.discount {
  border: 3px solid red;
}
</style>
