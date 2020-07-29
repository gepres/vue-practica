<template>
  <div ref="myDraggable" class="draggable">
     <v-btn  @click="clickbtn" class="mx-2" fab dark large color="cyan">
      <v-icon dark>fas fa-shopping-cart</v-icon>
    </v-btn>
  </div>
     
</template>

<script>
import interact from "interactjs";
  export default {
    data() {
    return {
      screenX: 0,
      screenY: 0
    };
  },
  created(){

  },
  mounted: function() {
    let myDraggable = this.$refs.myDraggable;
    this.initInteract(myDraggable);
  },
  methods: {
    clickbtn(){
      console.log(this.$store.state.btnCart);
      if(this.$store.state.btnCart){
        return;
      }
      this.$router.push('/publicar')
    },
    initInteract(selector) {
      interact(selector).draggable({
        // enable autoScroll
        autoScroll: true,

        onstart: this.onDragStart,
        // call this function on every dragmove event
        onmove: this.dragMoveListener,
        // call this function on every dragend event
        onend: this.onDragEnd
      });
    },
    dragMoveListener: function(event) {
      const target = event.target;

              const dataX = target.getAttribute('data-x');
              const dataY = target.getAttribute('data-y');
              const initialX = parseFloat(dataX) || 0;
              const initialY = parseFloat(dataY) || 0;

              const deltaX = event.dx;
              const deltaY = event.dy;

              const newX = initialX + deltaX;
              const newY = initialY + deltaY;

              target
                .style
                .transform = `translate(${newX}px, ${newY}px)`;

              target.setAttribute('data-x', newX);
              target.setAttribute('data-y', newY);
    },
    onDragStart(event) {
      console.log('Arrastar',this.$store.state.btnCart);
      this.$store.state.btnCart = true
    },
    onDragEnd: function(event) {
      setTimeout(() => {
         this.$store.state.btnCart = false
      }, 500);
      console.log('soltar',this.$store.state.btnCart);
    }
  }
  }
</script>

<style lang="scss" scoped>
.draggable {
  position: absolute;
  touch-action: none;
    user-select: none;
}
</style>