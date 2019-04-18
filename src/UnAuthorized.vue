<template>
  <div id="app">
      <h1>UNAuthorized GAxios Client</h1>
  </div>
</template>

<script>

import GAxios from '@/utils/GAxios.js';

export default {
  name: 'UnAuthorized',

  data: function(){
    return{
      supportedMethods: ['GET', 'POST', 'PUT', 'DELETE']
    }
  },

  mounted: function(){

    // Parameters
    let method = 'POST';
    //let URI = '';
    let URI = 'http://localhost:8000/api/login/';
    let body = {
      "username":"artist1",
      "password":"artist1artist1"

    }

    // Requests
    console.log('*** Iniciando... ***');

    if(method != undefined && method != null && this.supportedMethods.includes(method.toUpperCase())){

      if(method.toUpperCase() == 'GET'){

        GAxios.get(URI,body).then(response => {
          console.log('*** Se ha obtenido una respuesta de BackEnd ***');
          console.log(response);
        }).catch( err => {
          console.log('*** ERROR: La respuesta no ha sido satisfactoria ***');
          console.log(err);
        }).then( x => {
          console.log('*** FIN ***');
        })

      }else if(method.toUpperCase() == 'POST'){

        GAxios.post(URI,body).then(response => {
          console.log('*** Se ha obtenido una respuesta de BackEnd ***');
          console.log(response);
        }).catch( err => {
          console.log('*** ERROR: La respuesta no ha sido satisfactoria ***');
          console.log(err);
        }).then( x => {
          console.log('*** FIN ***');
        })

      }else if(method.toUpperCase() == 'PUT'){

        GAxios.put(URI,body).then(response => {
          console.log('*** Se ha obtenido una respuesta de BackEnd ***');
          console.log(response);
        }).catch( err => {
          console.log('*** ERROR: La respuesta no ha sido satisfactoria ***');
          console.log(err);
        }).then( x => {
          console.log('*** FIN ***');
        })

      }else if(method.toUpperCase() == 'DELETE'){
        GAxios.delete(URI,body).then(response => {
          console.log('*** Se ha obtenido una respuesta de BackEnd ***');
          console.log(response);
        }).catch( err => {
          console.log('*** ERROR: La respuesta no ha sido satisfactoria ***');
          console.log(err);
        }).then( x => {
          console.log('*** FIN ***');
        })
      }
    }

  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
