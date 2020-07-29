<template>
  <div>
    <v-app-bar
      color="deep-purple accent-4"
      dense
      dark
    >
      <v-toolbar-title>Lugar para Practicas</v-toolbar-title>
      <v-spacer></v-spacer>
      <ul>
        <li>
          <router-link to="/">Home</router-link>
        </li>
        <li>
          <router-link to="/publicar">Publicar</router-link>
        </li>
        <li>
          <router-link to="/interact">Interact</router-link>
        </li>
         <li>
          <router-link to="/draggable">draggable</router-link>
        </li>
      </ul>
     

    </v-app-bar>
  </div>
</template>

<script>
  export default {
    
  }
</script>

<style lang="scss" scoped>
ul{
  display: flex;
  & li {
    list-style: none;
    margin-left: 1rem;
   & a{
      color:#fff;
      text-decoration: none;
   }
  }
}
</style>