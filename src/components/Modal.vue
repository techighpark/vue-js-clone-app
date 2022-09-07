<template lang="">
  <div class="black-bg" v-if="modal === true">
    <div class="white-bg">
      <h4>{{ importProducts[clickedProducts].title }}</h4>
      <div>{{ importProducts[clickedProducts].content }}</div>
      <label for="amount">Amount : </label>
      <input
        @input="amount = $event.target.value"
        id="amount"
        name="amount"
        :value="amount"
      />
      <input v-model.number="amount" id="amount" name="amount" />
      <div>
        <textarea v-model="textarea" name="textarea"></textarea>
      </div>
      <div>
        Fee : {{ importProducts[clickedProducts].price.toLocaleString() }} won
      </div>
      <div>
        Total fee :
        {{ (importProducts[clickedProducts].price * amount).toLocaleString() }}
        won
      </div>
      <img
        class="room-img"
        :src="importProducts[clickedProducts].image"
        alt=""
      />
      {{ textarea }}

      <button @click="closeModal">close</button>
      <button @click="$emit('emitClose')">close</button>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Modal',
  data() {
    return {
      amount: 1,
      textarea: '',
    };
  },
  props: {
    importProducts: Object,
    clickedProducts: Number,
    modal: {
      type: Boolean,
      required: true,
    },
    closeModal: {
      type: Function,
      required: true,
    },
  },
  watch: {
    amount(newParam, oldParam) {
      if (newParam.includes(' ')) {
        alert('White space nono.');
        const whiteRule = newParam.replace(' ', '');
        this.amount = whiteRule;
      } else if (isNaN(newParam) === true) {
        alert('Enter only number.');
        this.amount = oldParam;
      } else if (newParam > 12) {
        alert('amount could not exceed 12.');
        this.amount = oldParam;
      }
    },
  },
  created() {
    // console.log(this.modal);
  },
};
</script>
<style lang=""></style>
