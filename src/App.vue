<template>
  <v-app>
    <Header></Header>
    <v-content></v-content>
  </v-app>
</template>

<script>
import Header from "./components/Header.vue";
export default {
  name: "App",
  data() {
    return {
      // TODO
    };
  },
  components: {
    Header
  }
};
</script>
