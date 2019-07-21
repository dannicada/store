<template>
  <div>
    
    <!-- Links are to sibling routes -->
   
    <v-btn outline color="indigo" to="/admin">View Products</v-btn>
    <v-btn outline color="indigo" to="/admin/new">New Product</v-btn>
    <!-- Outlet for children routes -->
    <router-view></router-view>




  </div>
</template>