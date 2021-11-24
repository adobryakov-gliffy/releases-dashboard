<template>
  <v-app>
        <img
          alt="Perforce"
          height="30"
          style="margin: 20px"
          contain
          min-width="200"
          src="https://www.perforce.com/themes/custom/themekit/logo.svg"
          width="200"
        />

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
