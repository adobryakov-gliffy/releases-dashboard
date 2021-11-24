<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        
      <v-spacer></v-spacer>
        <v-img
          alt="Perforce"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="200"
          src="https://www.perforce.com/themes/custom/themekit/logo.svg"
          width="200"
        />
      </div>

      <v-spacer></v-spacer>


    </v-app-bar>

    <v-main>
      <HelloWorld/>
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    HelloWorld,
  },

  data: () => ({
    //
  }),
};
</script>
