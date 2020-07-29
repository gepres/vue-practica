<template>
  <div>
    <v-container>
      <v-row class="justify-center">
        <v-col cols="12" xs="12" sm="12" md="6" lg="6">
          <v-form class="text-right" ref="form" v-model="valid" lazy-validation @submit.prevent="savepost" enctype="multipart/form-data">
            <v-row>
              <v-col cols="12">
                <h1 class="text-center grey--text text--darken-2">Postea2 lo que más te guste</h1>
              </v-col>
              <v-col cols="12" class="py-0">
                <v-text-field
                  v-model="post.title"
                  :rules="[rules.required]"
                  type="text"
                  label="Titulo"
                  required
                  dense
                  outlined
                  color="primero"
                ></v-text-field>
              </v-col>
              <v-col cols="12" class="py-0">
                <!-- @change="reconocerFoto" -->
                <v-file-input
                  @change="reconocerFoto"
                  v-model="post.file"
                  prepend-icon="fas fa-camera"
                  label="Imagen del Post"
                  outlined dense
                  :rules="[rules.required]"
                  accept="image/png, image/jpeg"
                  show-size
                  multiple
                  chips
                  >
                </v-file-input>
                <!-- <input type="file" ref="file" accept="image/png, image/jpeg" name="imagen" @change="onSelect" multiple> -->
              </v-col>
              <v-col cols="12" class="d-flex" v-if="post.file">
                 <img src="" :id="'photo-'+index"  width="200"  v-for="(item, index) in post.file" :key="index">
              </v-col>
              <v-col cols="12" class="py-0">
                <v-textarea
                  outlined
                  
                  label="Descripción"
                  v-model="post.description"
                  :rules="[rules.required]"
                   required
                ></v-textarea>
              </v-col>
            </v-row>

            <v-btn
              :disabled="!valid"
              rounded
              type="submit"
            >
            <span v-if="cargaImg">
                 <v-progress-circular
                indeterminate
                color="primary"
              ></v-progress-circular>
              Cargando
              </span>
              <span v-else>Postear</span> 
            </v-btn>

    
          </v-form>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import axios from 'axios'
import Swal from 'sweetalert2'
  export default {
    data(){
      return {
        valid: true,
        post:{
          title:'',
          description: '',
          file:null,
          cargaImg: false
        },
        rules:{
          required: v=> !!v || 'El campo es requerido'
        }
      }
    },
    methods:{
      async reconocerFoto(){
        const array = this.post.file

        setTimeout(() => { 
          for (let index = 0; index < array.length; index++) {
          const element = array[index];
           this.showImage(element,index)
        }
         }, 1000);
    
      },
      async showImage(item,index){
        // console.log(index);
        const id = 'photo-'+index
        
        const target = document.getElementById(id)
        // console.log(target);
        
        const fr = new FileReader();
        fr.onload = function(){
            target.src = fr.result;
        }
        fr.readAsDataURL(item);
      },
       onSelect(){
        const file = this.$refs.file.files
        const fileArray = Object.values(file);
        
        // console.log(file.split(','))
        
        this.post.file = fileArray
        // this.seletedFileName = file.name
        
      },
      async savepost () {
        this.$refs.form.validate()
        this.cargaImg = true
        const formData = new FormData()
        formData.append('title',this.post.title)
        for (let index = 0; index < this.post.file.length; index++) {
          const element = this.post.file[index];
          formData.append('imagen',element)
        }
        formData.append('description',this.post.description)
        // console.log(this.post.file);
        try {;
          const res = await axios.post(`${this.$store.state.baseURL}/api/photo`,formData)
          if(res.status === 200){
            await Swal.fire({
             icon:'success',
              title:'Post creado correctamente.',
            })
            this.cargaImg = false
            this.$router.push('/')
          }
        } catch (error) {
          console.log(error)
          if(error.response){
            Swal.fire({
              icon:'error',
              title:error.response.data.error,
              text:'Tiene que pesar menos de 2MB, vuelva a intentarlo'
            })
          }else{
            Swal.fire({
              icon:'error',
              title:'Hubo un error',
              text:'Hubo un error'
            })
          }
        }
      }
    },
    computed:{
      showPhoto(item){
        return item
      }
    }
  }
</script>

<style lang="css">

</style>
