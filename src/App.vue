<template>
 <div>
   <v-app> 
    <Navigation />
    <Appbar />
    <v-content>
      <router-view/>
    </v-content>
   </v-app>
  </div>  
</template>

<script>
import Navigation from './components/Navigation';
import Appbar from './components/Appbar'

export default {
  name: 'App',

  components: {
    Navigation,Appbar
  },

  data: () => ({
    //
  }),
};
</script>
