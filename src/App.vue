<template>
  <v-app>
    <!-- <v-app-bar app color="primary" dark> </v-app-bar> -->

    <v-main>
      <router-view> </router-view>
    </v-main>
  </v-app>
</template>

<script>
// import Eyes from "@/components/Eyes.vue";

export default {
  name: "App",

  components: {
    // Eyes,
  },
  data: () => ({
    //
  }),
};
</script>
