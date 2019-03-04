<template>
  <v-item-group>
    <v-container grid-list-md fluid d-flex>
      <v-layout row-md>
        <v-flex xs12 md12>
          <v-item>
            <v-hover>
              <v-card slot-scope="{ hover }" class="mx-auto" color="grey lighten-4" max-width="600">
                <v-img :aspect-ratio="16/9" :src="items.image">
                  <v-expand-transition>
                    <div
                      v-if="hover"
                      class="d-flex transition-fast-in-fast-out info darken-2 v-card--reveal display-3 white--text"
                      style="height: 100%;"
                    >{{formatPrice(items.price)}}</div>
                  </v-expand-transition>
                </v-img>
                <v-card-text class="pt-4" style="position: relative;">
                  <v-btn
                    absolute
                    color="info"
                    class="white--text"
                    fab
                    large
                    right
                    top
                    @click="addToCart"
                  >
                    <v-icon>mdi-cart</v-icon>
                  </v-btn>
                  <div class="font-weight-bold title mb-2">{{items.categories}}</div>
                  <h3 class="display-1 font-weight-light orange--text mb-2">{{items.name}}</h3>
                  <div class="font-weight-light title mb-2">{{items.desc}}</div>
                </v-card-text>
              </v-card>
            </v-hover>
          </v-item>
        </v-flex>
      </v-layout>
    </v-container>
  </v-item-group>
</template>
<style>
.v-card--reveal {
  align-items: center;
  bottom: 0;
  justify-content: center;
  opacity: 0.5;
  position: absolute;
  width: 100%;
}
</style>
<script>
export default {
  name: "Products",
  props: {
    items: {
      type: Object,
      required: true
    },
    cart: {
      type: Array
    }
  },
  data() {
    return {};
  },
  methods: {
    addToCart() {
      this.cart.push(this.items); // push item to cart
    },
    formatPrice(cents) {
      return (cents / 100).toLocaleString("en-US", {
        style: "currency",
        currency: "USD"
      });
    }
  }
};
</script>
