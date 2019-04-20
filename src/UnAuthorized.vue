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
      supportedMethods: ['GET', 'POST', 'PUT', 'DELETE'],
      supportedLanguages: ['en', 'es'],
    }
  },

  mounted: function(){

    // Parameters
    //let URI = '';
    let URI = 'http://localhost:8000/api/login/';
    let method = 'POST';
    let language = 'es';

    // Body: Only for POST and PUT
    let body = {
      "username":"artist1",
      "password":"artist1artist1"

    }

    // Parameters: Only for GET
    let parameters = {
      "sort": "true" 
    }

    // ----- REQUESTS -----------
    console.log('*** Iniciando... ***');

    if(method && this.supportedMethods.includes(method.toUpperCase()) && 
      language && this.supportedLanguages.includes(language.toLowerCase())){

      GAxios.defaults.headers.common['Accept-Language'] = language.toLowerCase();

      if(method.toUpperCase() == 'GET'){

        GAxios.get(URI,{
          params: parameters,
        }).then(response => {
          console.log('*** Se ha obtenido una respuesta de BackEnd ***');
          console.log(response);
        }).catch( err => {
          console.log('*** ERROR: La respuesta no ha sido satisfactoria ***');
          console.log(err);
        }).then( x => {
          console.log('*** FIN ***');
        })

      }else if(method.toUpperCase() == 'POST'){

        GAxios.post(URI, body).then(response => {
          console.log('*** Se ha obtenido una respuesta de BackEnd ***');
          console.log(response);
        }).catch( err => {
          console.log('*** ERROR: La respuesta no ha sido satisfactoria ***');
          console.log(err);
        }).then( x => {
          console.log('*** FIN ***');
        })

      }else if(method.toUpperCase() == 'PUT'){

        GAxios.put(URI, body).then(response => {
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
