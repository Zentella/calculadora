<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <h4 class="texto">Calculadora</h4>
    </v-app-bar>

    <v-main>
      <router-view />
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'App',

  data: () => ({
    //
  })
}
</script>

<style scoped>
.texto {
  text-align: center;
  margin: auto;
}
</style>
