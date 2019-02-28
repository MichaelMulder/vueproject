<template>
  <v-menu>
    <v-btn round color="primary" slot="activator" @click="totalPrice">
      <v-badge left color="red" v-show="cart.length > 0">
        <span slot="badge">{{cart.length}}</span>
      </v-badge>
      <v-icon>mdi-cart</v-icon>
    </v-btn>
    <v-card>
      <v-list v-for="(item, id) in cart" :key="id">
        <v-list-tile>
          <v-list-tile-content>
            <v-list-tile-title>{{item.name}}</v-list-tile-title>
            <v-list-tile-sub-title>{{formatPrice(item.price)}}</v-list-tile-sub-title>
          </v-list-tile-content>
          <v-list-tile-action>
            <v-btn>Remove</v-btn>
          </v-list-tile-action>
        </v-list-tile>
      </v-list>
      <v-divider></v-divider>
      <v-list>
        <v-list-tile>
          <v-list-tile-title>{{total}} hello</v-list-tile-title>
        </v-list-tile>
      </v-list>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn flat @click="menu = false">Cancel</v-btn>
        <v-btn color="primary" flat>Check Out</v-btn>
      </v-card-actions>
    </v-card>
  </v-menu>
</template>

<script>
export default {
  name: "Cart",
  props: {
    cart: {
      type: Array
    }
  },
  data() {
    return {
      // TODO
    };
  },
  methods: {
    formatPrice(cents) {
      return (cents / 100).toLocaleString("en-US", {
        style: "currency",
        currency: "USD"
      });
    }
  }
};
</script>
