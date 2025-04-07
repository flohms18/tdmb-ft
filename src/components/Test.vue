<template>
    <div>
      <h1>Enter the name of your favorite movie!</h1>
      {{ james }}
    </div>

  </template>
  
  <script>

  import axios from 'axios';

export default {
    name: 'Test',
    methods : {
        GoTom() {
            console.log("James Bond!")
        }
    },
    mounted() {
        this.GoTom()
    },

    data() {
        return {
            james : 'Me Voilà!'
        }

    }

}

  

  
  </script>
  