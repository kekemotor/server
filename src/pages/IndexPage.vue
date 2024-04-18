<template>
  <q-page class="flex flex-center">
    <mobSelect @select = "mobSelect"/><q-input @update:model-value="inputCount" type="number" v-model="count"></q-input>
  </q-page>
  <p>{{ mainString.name }} {{ mainString.mob }}</p>
  <h1>{{ this.mob  }}</h1>
  <p>{{ this.count }}</p>
</template>

<script>
import { computed, ref } from 'vue'
import { useStore } from 'vuex'
import mobSelect from "../components/mobSelect.vue"
export default {
  components:{
    mobSelect
  },data(){
    return{
      mainString:{
        name:"/summon",
        mob:"",
      },
      mob:"",
      count:0
    }
  }
}

</script>
