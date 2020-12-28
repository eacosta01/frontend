<template>
  <div id="tope">
    <!-- 
      https://getbootstrap.com/docs/4.0/components/navbar/ 
      https://getbootstrap.com/docs/4.0/getting-started/introduction/
    -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <a class="navbar-brand" href="https://unam.mx" target="_blank"><img src='/logo.png' width="64px;" /></a>

      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item active">
            <a class="nav-link" href="#" @click="goHome"><b>¿En qué te ayudo?</b> <span class="sr-only">(current)</span></a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#" @click="goList">Inicio</a>
          </li>
          
          <li class="nav-item">
           <a class="nav-link" href="#" @click="goList">Preguntas</a>
          </li>
        </ul>

      </div>
      
    </nav>
  </div>
</template>

<script>

   import router from './router';
import store from './store'

export default {
    name: "Sidebar",
    data: function () {
        return {
          usr: ".",
          url: process.env.VUE_APP_URL, 
          title: process.env.VUE_APP_TITLE 
        }
    },
    computed: {
      firmado: function() {
        return store.state.firmado;
      },
      currentRouteName: function() {
         return this.$route.path;
      }
    },  
    methods: {
      goHome: function() {router.push('/');},
      goLogin: function() {
        store.commit('setState', '');
        store.commit('setFirmado', false);
        this.checa('/ui/login');
      },
      goForgot: function() {this.checa('/ui/forgot');},
      goRegistro: function() {this.checa('/ui/registro');},
      goList: function() {this.checa('/ui/list');},

      goAviso: function() {this.checa('/ui/aviso');},
      goPreguntas: function() {this.checa('/ui/preguntas');},
      goVideos: function() {this.checa('/ui/video');},
      goUpload: function() {this.checa('/ui/upload');},
      goPerfil: function() {this.checa('/ui/perfil');},
      goCambia: function() {this.checa('/ui/cambiar-clave');},

      checa: function(url) {
        if(this.currentRouteName===url) {      
          console.log('same place');
        } else {
          router.push(url);
        }
      }
    }
}


</script>

<style scoped>
header {
background-color: darkgrey;
padding: 10 px;
height: 50px;
text-align: center;
color: #ffffff;

}
</style>
