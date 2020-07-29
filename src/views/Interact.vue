<template>
  <div>
    <h1>Interact.js 3</h1>
    <btnCart />
    <!-- <v-btn  ref="myDraggable" id="idmove" class="mx-2 onmove" fab dark large color="cyan">
      <v-icon dark>fas fa-shopping-cart</v-icon>
    </v-btn> -->
  </div>
</template>

<script>
  import interact from 'interactjs'
  import btnCart from '@/components/btnCart.vue'
  export default {
    components:{btnCart},
    data() {
      return {
        // valuemove: false
      }
    },
    // mounted: function() {
    //   this.onmove();
    //   this.captarEnvio()
    // },
    // methods: {
    //   enviar() {
    //     console.log(this.valuemove);
    //     console.log('enviar')
    //   },
    //   captarEnvio(){
    //     const btn = document.getElementById('idmove')
    //     btn.addEventListener('click', () => {
    //     if(this.valuemove){  
    //       return;
    //     }
    //     this.enviar()
    //   })
    //   },
    //   onmove() {
    //     interact('.onmove').draggable({
    //         onstart: this.onDragStart,
    //         onmove: function (event) {
    //           const target = event.target;

    //           const dataX = target.getAttribute('data-x');
    //           const dataY = target.getAttribute('data-y');
    //           const initialX = parseFloat(dataX) || 0;
    //           const initialY = parseFloat(dataY) || 0;

    //           const deltaX = event.dx;
    //           const deltaY = event.dy;

    //           const newX = initialX + deltaX;
    //           const newY = initialY + deltaY;

    //           target
    //             .style
    //             .transform = `translate(${newX}px, ${newY}px)`;

    //           target.setAttribute('data-x', newX);
    //           target.setAttribute('data-y', newY);
    //         },
    //         onend:this.onDragEnd
    //       })
    //   },
    //   onDragStart(event) {
    //     this.valuemove = true
    //     console.log('arrastrando')
    //   },
    //   onDragEnd(event) {
    //     setTimeout(() => {
    //     this.valuemove = false
    //     }, 1000);
    //   console.log('soltar')
    //   }
    // }
  }
</script>

<style lang="scss" scoped>
  .onmove {
    touch-action: none;
    user-select: none;
  }
</style>