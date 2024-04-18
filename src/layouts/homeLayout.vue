<template>
    <q-layout view="lHh Lpr lFf"> 
        <p>Привет! Это сайт для создания комманд в майнкрафте! Вот список комманд</p>
        <a href="/command/give">give</a>
  
      <q-page-container>
        <router-view />
      </q-page-container>
    </q-layout>
  </template>
  
  <script>
  import { ref } from 'vue'
  import EssentialLink from 'components/EssentialLink.vue'
  
  export default{
    data(){
      return{
        
      }
    },
    
  }
  
  

  </script>
  

