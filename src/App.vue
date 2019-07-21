<template>
 <div id='app'>
<v-app>
  <v-toolbar app>
  <v-btn to="/">Home</v-btn>
  <v-btn to="/admin">Admin</v-btn>
  <v-spacer></v-spacer>
  <v-btn to="/cart">Cart</v-btn>
  </v-toolbar>
  <v-content>
    <v-container fluid>
      <router-view></router-view>
    </v-container>
  </v-content>
  <v-footer app></v-footer>
</v-app>
  </div>
</template>



<script>
export default {
  name: 'App',
};
</script>

<style>

</style>
