<template>
  <q-layout>
    <q-page-container>
    <q-page class="flex flex-center"> 
      <mobSelect @select = "mobSelect"/><q-input @update:model-value="inputCount" type="number" v-model="count"></q-input>
    </q-page>
  </q-page-container>
  </q-layout>
  <p v-for="item in items">{{ "item"  }}</p>
</template>

<script>
import { computed, ref } from 'vue'
import { useStore } from 'vuex'
import mobSelect from "../components/mobSelect.vue"

export default {
  components: {
    mobSelect
  },
  setup() {
    const $store = useStore()
    const items = $store.getters["myStore/getItems"]
    let intmsA = [...items]
    console.log(itemsA)
    console.log($store)

    return {
      $store,
      items,
      mobSelect,
    }
  },
  data() {
    return {
      mainString: {
        name: "/summon",
        mob: "",
      },
      mob: "",
      count: 0
    }
  }
}
</script>
