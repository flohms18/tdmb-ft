<template>
    <div>
      <h1>Enter the name of your favorite movie!</h1>
      <input placeholder="Enter the name of our favorite movie!" v-model="UserMovie">
      <button @click="RequestMovie">OK</button>
      <p> {{  SavedMovie }}</p>
    </div>

  </template>
  
  <script>

import axios from 'axios';

export default {
    name: 'Test',
    data() {
        return {
            UserMovie : '',
            SavedMovie : ''
        }

    },
    methods : {
        RequestMovie() {
            this.SavedMovie= this.UserMovie
        }
    },
    mounted() {
        
    }

    

}

  

  
  </script>
  