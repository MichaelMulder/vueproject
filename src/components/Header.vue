<template>
  <header>
    <v-toolbar app dark>
      <v-toolbar-title class="headline text-uppercase">
        <span class="font-weight-bold">
          <v-icon>mdi-robot</v-icon>Roboto's Emporiem&trade;
        </span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-flex xsm12 sm6 md3>
        <v-text-field
          label="Search"
          prepend-icon="mdi-magnify"
          single-line
          clearable
          small
          :value="value"
          @input="$emit('input', $event)"
        ></v-text-field>
      </v-flex>
      <v-menu open-on-hover transition="scale-transiton" :close-on-content-click="false">
        <v-btn round color="primary" slot="activator">
          <v-badge left color="red" v-show="cart.length > 0">
            <span slot="badge">{{cart.length}}</span>
          </v-badge>
          <v-icon>mdi-cart</v-icon>
        </v-btn>
        <v-card>
          <v-list v-for="item in cart" :key="item.id">
            <v-list-tile>
              <v-list-tile-content>
                <v-list-tile-title>{{item.name}}</v-list-tile-title>
                <v-list-tile-sub-title>{{formatPrice(item.price)}}</v-list-tile-sub-title>
              </v-list-tile-content>
              <v-list-tile-action>
                <v-icon @click="removeItem(item)">mdi-cart-remove</v-icon>
              </v-list-tile-action>
            </v-list-tile>
          </v-list>
          <v-divider></v-divider>
          <v-list>
            <v-list-tile>
              <v-list-tile-title>{{formatPrice(total)}}</v-list-tile-title>
            </v-list-tile>
          </v-list>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="primary" flat>Check Out</v-btn>
          </v-card-actions>
        </v-card>
      </v-menu>
    </v-toolbar>
  </header>
</template>

<script>
export default {
  name: "Header",
  props: {
    cart: Array,
    total: Number,
    value: {
      default: "",
      type: String
    }
  },
  data() {
    return {};
  },
  methods: {
    formatPrice(cents) {
      return (cents / 100).toLocaleString("en-US", {
        style: "currency",
        currency: "USD"
      });
    },
    removeItem(item) {
      this.cart.splice(this.cart.indexOf(item), 1);
    }
  }
};
</script>