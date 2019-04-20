<template>
  <div id="app">
      <h1>Authorized GAxios Client</h1>
  </div>
</template>

<script>

import GAxios from '@/utils/GAxios.js';

export default {
  name: 'Authorized',

  data: function(){
    return{
      supportedMethods: ['GET', 'POST', 'PUT', 'DELETE'],
      supportedLanguages: ['en', 'es'],
    }
  },

  mounted: function(){
    
    //766a98b2070b3deabfeaac5df832fd198533c60d customer1
    //a30e970fb1373abd904ac7423ee932a1ea0c6d69

    // Parameters
    let URI = 'http://localhost:8000/offer/';    
    let method = 'POST';
    let token = 'bbe6ccdf208ef31c5530783298ad20b19bcccc01';
    let language = 'es';

    // Body: Only for POST and PUT
    let body = {

    "type": "PHOTO",
    "link": "http://fsdg.com",
    "description": "Hey",
    "portfolio": 5

    };

    // Parameters: Only for GET
    let parameters = {
      "sort" : "asc"
    }

    // ----- REQUESTS -----------
    console.log('*** Iniciando... ***');

    if(method && this.supportedMethods.includes(method.toUpperCase()) && 
      language && this.supportedLanguages.includes(language.toLowerCase())){
      
      var authorizedGAxios = GAxios;
      authorizedGAxios.defaults.headers.common['Authorization'] = 'Token ' + token;
      authorizedGAxios.defaults.headers.common['Accept-Language'] = language.toLowerCase();

      if(method.toUpperCase() == 'GET'){

        authorizedGAxios.get(URI,{
          params: parameters
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

        authorizedGAxios.post(URI, body).then(response => {
          console.log('*** Se ha obtenido una respuesta de BackEnd ***');
          console.log(response);
        }).catch( err => {
          console.log('*** ERROR: La respuesta no ha sido satisfactoria ***');
          console.log(err);
        }).then( x => {
          console.log('*** FIN ***');
        })

      }else if(method.toUpperCase() == 'PUT'){

        authorizedGAxios.put(URI, body).then(response => {
          console.log('*** Se ha obtenido una respuesta de BackEnd ***');
          console.log(response);
        }).catch( err => {
          console.log('*** ERROR: La respuesta no ha sido satisfactoria ***');
          console.log(err);
        }).then( x => {
          console.log('*** FIN ***');
        })

      }else if(method.toUpperCase() == 'DELETE'){
        
        authorizedGAxios.delete(URI,body).then(response => {
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

  },
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
