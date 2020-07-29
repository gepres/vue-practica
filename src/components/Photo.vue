<template>
 <v-col cols="4">
   <v-card
    class="mx-auto"
    max-width="400"
  >
    <v-carousel
    cycle
    height="250"
    hide-delimiter-background
    show-arrows-on-hover
  >
    <v-carousel-item
      v-for="(item, i) in arrayImage"
      :key="i"
      :src="item"
    >
    </v-carousel-item>
    </v-carousel>

    <v-card-subtitle class="pb-0">Number 10</v-card-subtitle>

    <v-card-text class="text--primary">
      <div>{{photo.title}}</div>

      <div>{{photo.description}}</div>
    </v-card-text>
  </v-card>
 </v-col>
</template>

<script>
  export default {
    props:['photo'],
    data(){
      return {

      }
    },
    computed:{
      arrayImage(){
        let string = this.photo.image_url
        return string.split(',')
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>