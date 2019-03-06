<template>
  <v-app>
    <Header :cart="cart" :total="total" v-model="search"></Header>
    <v-spacer></v-spacer>
    <v-spacer></v-spacer>
    <v-spacer></v-spacer>
    <Products :cart="cart" :items="item" v-for="item in filteredProducts" :key="item.id"></Products>
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
      store: items,
      search: ""
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
    filteredProducts() {
      return this.store.filter(item => {
        const regex = new RegExp(this.search, "gi");
        return item.name.match(regex) || item.categories.match(regex);
      });
    }
  }
};
</script>
