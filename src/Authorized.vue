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
      supportedMethods: ['GET', 'POST', 'PUT', 'DELETE']
    }
  },

  mounted: function(){
    //766a98b2070b3deabfeaac5df832fd198533c60d customer1
    //a30e970fb1373abd904ac7423ee932a1ea0c6d69
    // Parameters
    let method = 'POST';
    let token = 'a30e970fb1373abd904ac7423ee932a1ea0c6d69';
    let URI = '/portfolioModule/';
    let body = {


    "type": "PHOTO",
    "link": "http://fsdg.com",
    "description": "Hey",
    "portfolio": 5

    };

    // Requests
    console.log('*** Iniciando... ***');

    if(method != undefined && method != null && this.supportedMethods.includes(method.toUpperCase())){
      if(method.toUpperCase() == 'GET'){

        var authorizedGAxios = GAxios;
        authorizedGAxios.defaults.headers.common['Authorization'] = 'Token ' + token;

        authorizedGAxios.get(URI,body).then(response => {
          console.log('*** Se ha obtenido una respuesta de BackEnd ***');
          console.log(response);
        }).catch( err => {
          console.log('*** ERROR: La respuesta no ha sido satisfactoria ***');
          console.log(err);
        }).then( x => {
          console.log('*** FIN ***');
        })

      }else if(method.toUpperCase() == 'POST'){

        var authorizedGAxios = GAxios;
        authorizedGAxios.defaults.headers.common['Authorization'] = 'Token ' + token;

        authorizedGAxios.post(URI,body).then(response => {
          console.log('*** Se ha obtenido una respuesta de BackEnd ***');
          console.log(response);
        }).catch( err => {
          console.log('*** ERROR: La respuesta no ha sido satisfactoria ***');
          console.log(err);
        }).then( x => {
          console.log('*** FIN ***');
        })

      }else if(method.toUpperCase() == 'PUT'){

        var authorizedGAxios = GAxios;
        authorizedGAxios.defaults.headers.common['Authorization'] = 'Token ' + token;

        authorizedGAxios.put(URI,body).then(response => {
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
