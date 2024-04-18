<template>
    <q-select
      v-model="model"
      use-input
      input-debounce="0"
      label="Simple filter"
      :options="options"
      @filter="filterFn"
      @update:modelValue="onSelect"
      style="width: 250px"
    />
  </template>
  
  <script>
  import { computed, ref, onMounted, getCurrentInstance } from 'vue'
  import { useStore } from 'vuex'
  
  export default {

  

  }
  </script>
  