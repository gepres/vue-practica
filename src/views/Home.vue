<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <h2>Fotos</h2>
      </v-col>
      <Photo v-for="item in photos" :key="item._id" :photo="item" />
    </v-row>
  </v-container>
</template>

<script>
// @ is an alias to /src
import Photo from '@/components/Photo'
import axios from 'axios'
export default {
  name: 'Home',
  components:{Photo},
  data(){
      return {
        photos:[]
      }
  },
  created(){
    this.obtenerDatos()
  },
  methods:{
    async obtenerDatos(){
      const res = await axios.get(`${this.$store.state.baseURL}/api/photo`)
      this.photos = res.data
    }
  }
}
</script>
