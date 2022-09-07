<template>
  <!-- modal -->
  <div class="black-bg" v-if="modal === true">
    <div class="white-bg">
      <h4>{{ importProducts[clickedProducts].title }}</h4>
      <div>{{ importProducts[clickedProducts].content }}</div>
      <img
        class="room-img"
        :src="importProducts[clickedProducts].image"
        alt=""
      />
      {{ clickedProducts }}
      <button @click="closeModal">close</button>
    </div>
  </div>

  <div class="menu">
    <!-- <a>Home</a>
    <a>Products</a>
    <a>About</a>
    <a v-for="data in 3" :key="data">Home</a> -->
    <a v-for="(data, i) in menu" :key="i">{{ data }}</a>
  </div>
  <!-- binding object -->
  <!-- <div>
    Shopping Mall
    <h4 :style="style">{{ products[0] }} clone coding</h4>
    <p>{{ price1 }} dollar</p>
    <div>Reported : {{ reported }}</div>
    <button @click="reported++">Report</button>
  </div> -->
  <!-- biding computed -->
  <!-- <div>
    <h4 :style="classObject">vue clone coding</h4>
    <p>{{ price2 }} dollar</p>
    <button>Report</button>
  </div> -->

  <!-- Binding to Arrays -->
  <!-- <div>
    <h4 :style="[bgColor, color]">vue clone coding</h4>
    <p>{{ price2 }} dollar</p>
    <button>Report</button>
  </div> -->

  <!-- multiple conditional binding -->
  <!-- <div>
    <h4 :style="[bgColor, { color: style.color }]">vue clone coding</h4>
    <p>{{ price2 }} dollar</p>
    <button>Report</button>
  </div> -->
  <!-- personal -->
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
  <hr />
  <!-- apple coding -->
  <div v-for="(item, i) in importProducts" :key="i">
    <div @click="[openAppleModal(), (clickedProducts = i)]">
      <img :src="item.image" class="room-img" />
      <h4>{{ item.title }}</h4>
      <div>{{ item.content }}</div>
      <div>{{ item.price.toLocaleString() }}</div>
    </div>
    <div>Reported : {{ item.count }}</div>
    <button @click="increase(i)">Report</button>
  </div>

  <!-- <div v-for="({ title }, i) in forTest" :key="i">
    <h4>{{ title }}</h4>
  </div> -->
</template>

<script>
import products from '@/data/products';
export default {
  name: 'App',

  data() {
    return {
      // price1: 60,
      // price2: 70,
      // //binding object
      // style: { backgroundColor: 'black', color: 'red' },
      // //biding computed
      // hasError: true,
      // error: '123',
      // //Binding to Arrays
      // bgColor: 'backgroundColor:green',
      // color: 'color:orange',
      modal: false,
      clickedProducts: 0,
      importProducts: products,
      // products: [
      //   {
      //     place: 'Namsan',
      //     count: 0,
      //     imgSrc: require('./assets/images/room0.jpg'),
      //   },
      //   {
      //     place: 'Guseo',
      //     count: 0,
      //     imgSrc: require('./assets/images/room1.jpg'),
      //   },
      //   {
      //     place: 'Seomyeon',
      //     count: 0,
      //     imgSrc: require('./assets/images/room2.jpg'),
      //   },
      // ],
      // forTest: [{ title: '1111' }, { title: '2222' }, { title: '3333' }],
      menu: ['Home', 'Products', 'About'],
      reported: 0,
    };
  },
  methods: {
    // greet(event) {
    //   alert(`Hello ${this.reported}`);
    //   if (event) {
    //     alert(event.target.tagName);
    //   }
    // },
    increase(i) {
      this.importProducts.at(i).count++;
    },
    openModal(i) {
      this.modal = true;
      this.clickedProducts = i;
    },
    openAppleModal() {
      this.modal = true;
      console.log('appleModal');
    },
    closeModal() {
      this.modal = false;
    },
  },
  computed: {
    // classObject() {
    //   return {
    //     backgroundColor: this.hasError ? 'black' : 'red',
    //     color: this.error === 'true' ? 'red' : 'yellow',
    //   };
    // },
  },
  components: {},
};
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background-color: white;
  border-radius: 10px;
  padding: 20px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.room-img {
  box-sizing: border-box;
  width: 100%;
  margin-top: 100px;
  border: 3px solid orange;
  border-radius: 20px;
}

.menu {
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
  font-weight: 700;
}
</style>
