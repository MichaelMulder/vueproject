<template>
  <v-toolbar app dark>
    <v-toolbar-title class="headline text-uppercase">
      <span>Buy & Sell</span>
      <span class="font-weight-light">\Stuff</span>
    </v-toolbar-title>
    <v-spacer></v-spacer>
    <v-badge>
      <span slot="badge">{{cart}}</span>
      <v-icon @click="viewCart">mdi-cart</v-icon>
    </v-badge>
  </v-toolbar>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      // TODO
    };
  }
};
</script>