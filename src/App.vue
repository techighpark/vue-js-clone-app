<template>
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

  <div v-for="(item, i) in products" :key="i">
    <img :src="item.imgSrc" class="room-img" />
    <h4>{{ item.place }}</h4>
    <div>{{ item.count }}</div>
    <button @click="increase(i)">Report</button>
  </div>

  <!-- <div v-for="({ title }, i) in forTest" :key="i">
    <h4>{{ title }}</h4>
  </div> -->
</template>

<script>
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

      products: [
        {
          place: 'Namsan',
          count: 0,
          imgSrc: require('./assets/images/room0.jpg'),
        },
        {
          place: 'Guseo',
          count: 0,
          imgSrc: require('./assets/images/room1.jpg'),
        },
        {
          place: 'Seomyeon',
          count: 0,
          imgSrc: require('./assets/images/room2.jpg'),
        },
      ],
      // forTest: [{ title: '1111' }, { title: '2222' }, { title: '3333' }],
      menu: ['Home', 'Products', 'About'],
      reported: 0,
    };
  },
  methods: {
    greet(event) {
      alert(`Hello ${this.reported}`);
      if (event) {
        alert(event.target.tagName);
      }
    },
    increase(i) {
      console.log(i);
      this.products.at(i).count++;
    },
  },
  computed: {
    classObject() {
      return {
        backgroundColor: this.hasError ? 'black' : 'red',
        color: this.error === 'true' ? 'red' : 'yellow',
      };
    },
  },
  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.room-img {
  width: 100%;
  margin-top: 100px;
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
