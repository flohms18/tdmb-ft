<template>
    <div>
      <h1>Enter the name of your favorite movie!</h1> 
    </div>

  </template>
  
  <script>

export default {
    name: 'Test',
    methods : {
        GoTom() {
            console.log("James Bond!")
        }
    },
    mounted() {
        this.GoTom()
    }

}

  

  
  </script>
  