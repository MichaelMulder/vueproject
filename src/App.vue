<template>
  <v-app>
    <Header :cart="cart" :total="total"></Header>
    <v-spacer></v-spacer>
    <v-spacer></v-spacer>
    <Products :cart="cart" :items="item" v-for="item in store" :key="item.id"></Products>
  </v-app>
</template>

<script>
import Header from "./components/Header.vue";
import Products from "./components/Products.vue";
import items from "./items.js";
export default {
  name: "App",
  data() {
    return {
      cart: [],
      store: items
    };
  },
  components: {
    Header,
    Products
  },
  computed: {
    total() {
      // when the cart has something then find the total
      return this.cart
        .map(item => item.price) // find item prices
        .reduce((total, amount) => total + amount, 0); // add prices to total
    },
    findMatches(wordToMatch, items) {
      return items.filter(item => {
        const regex = new RegExp(wordToMatch, "gi");
        return item.name.match(regex) || item.catogories.match(regex);
      });
    }
  }
};
</script>
