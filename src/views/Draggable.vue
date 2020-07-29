<template>
  <v-container class="mt-5">
    <h1>Draggable</h1>
    <v-stage ref="stage"
      :config="configKonva"
      @dragstart="handleDragstart"
      @dragend="handleDragend">
    <v-layer ref="layer">
      <v-portal>
        <v-btn class="mx-2" fab dark large color="cyan">
        <v-icon dark>fas fa-shopping-cart</v-icon>
      </v-btn>
      </v-portal>
      <!-- <v-btn class="mx-2" fab dark large color="cyan">
        <v-icon dark>fas fa-shopping-cart</v-icon>
      </v-btn> -->
    </v-layer>
  </v-stage>
  </v-container>
</template>

<script>
import VueKonva from 'vue-konva'
const width = window.innerWidth;
const height = window.innerHeight;
export default {
data(){
  return {
    configKonva: {
        width: width,
        height: height
      },
      configCircle: {
        x: 100,
        y: 100,
        radius: 70,
        fill: "red",
        stroke: "black",
        strokeWidth: 4,
        draggable: true
      } 
  }
},
methods:{
  handleDragstart(e) {
      // save drag element:
      this.dragItemId = e.target.id();
      // move current element to the top:
      const item = this.list.find(i => i.id === this.dragItemId);
      const index = this.list.indexOf(item);
      this.list.splice(index, 1);
      this.list.push(item);
    },
    handleDragend(e) {
      this.dragItemId = null;
    }
}
}
</script>

<style>

</style>