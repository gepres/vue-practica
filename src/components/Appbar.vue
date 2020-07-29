<template>
  <div>
    <v-app-bar
      color="deep-purple accent-4"
      dense
      dark
    >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>P</v-toolbar-title>

      <v-text-field
            label="Outlined"
            placeholder="Placeholder"
            outlined
            hide-details
            full-width
            @focus="focusInput"
          ></v-text-field>

  <v-btn v-if="!focus" @click="focus = !focus" class="mx-2" fab dark small color="primary">
        <v-icon dark>fas fa-arrow-left</v-icon>
      </v-btn>
        <v-btn v-if="focus" class="mx-2" fab dark small color="primary">
      <v-icon dark>fas fa-folder</v-icon>
    </v-btn>
     <v-btn v-if="focus" class="mx-2" fab dark small color="primary">
      <v-icon dark>fas fa-folder</v-icon>
    </v-btn> 
    <v-btn v-if="focus" class="mx-2" fab dark small color="primary">
      <v-icon dark>fas fa-folder</v-icon>
    </v-btn>
      <v-spacer></v-spacer>

      <!-- <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>
      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-menu
        left
        bottom
      >
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            icon
            v-bind="attrs"
            v-on="on"
          >
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </template>

        <v-list>
          <v-list-item
            v-for="n in 5"
            :key="n"
            @click="() => {}"
          >
            <v-list-item-title>Option {{ n }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu> -->
    </v-app-bar>
  </div>
</template>

<script>
  export default {
    data(){
      return {
        focus:true
      }
    },
    methods:{
      focusInput(){
        this.focus = false
      }
    }
  }
</script>

<style lang="scss" scoped>

</style>