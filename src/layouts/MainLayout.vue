<template>
  <q-select
    filled
    v-model="model"
    use-input
    input-debounce="0"
    label="Simple filter"      
    @filter="filterFn"
    style="width: 250px"
    behavior="menu" 
    :options="options">

    <template v-slot:no-option>
      <q-item>
        <q-item-section class="text-grey">
          No results
        </q-item-section>
      </q-item>
    </template>
  </q-select>
  <enchants v-for="num in ColEnchants" v-bind:number="num"></enchants>
  <div><p v-for="enchant in this.$data.enchantsArr" >{{ enchant }} </p></div>

</template>

<script>
import { computed, ref } from 'vue'
import { useStore } from 'vuex'
import mobSelect from "../components/mobSelect.vue"
import enchants from "../components/enchants.vue"

export default {
  components: {
    mobSelect,enchants
  },
  methods:{
    setEnchants(enchant, lvl , index){
      console.log(enchant,lvl,index)
      this.$data.enchantsArr[index-1] = enchant
      console.log(this.$data.enchantsArr)
    }
  },

  setup() {
    const $store = useStore()
    let items = $store.getters["myStore/getItems"]
    items = JSON.parse(JSON.stringify(items))

    console.log(items)
    console.log($store)

    let names = items.map(item=>(item.name))
    let options = ref(names)

    console.log(names)
    return {
      names,
      $store,
      items,
      options,
      mobSelect,
      filterFn (val, update) {
        if (val === '') {
          update(() => {
            options.value = names
          })
          return
        }
        update(() => {
          const needle = val.toLowerCase()
          options.value = names.filter(v => v.toLowerCase().indexOf(needle) > -1)
        })
       }
    }
},
  data() {
    return {
      enchantsArr:ref([]),
      ColEnchants:3,

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
