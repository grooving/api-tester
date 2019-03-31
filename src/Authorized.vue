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
      supportedMethods: ['GET', 'POST', 'PUT']
    }
  },

  mounted: function(){

    // Parameters
    let method = 'POST';
    let token = 'bbe6ccdf208ef31c5530783298ad20b19bcccc01';
    let URI = 'http://localhost:8000/offer/';
    let body = {
	    "description": "This is a description",
	    "date": "2019-05-10T10:00:00",
	    "paymentPackage_id": "1",
	    "eventLocation_id": "1"
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
