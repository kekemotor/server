<template>
  <q-select
    filled
    v-model="model"
    use-input
    input-debounce="0"
    label="Зачарование"      
    @filter="filterFn"
    style="width: 250px"
    behavior="menu" 
    :options="options"
    @update:model-value="changecEnchant"
  >
    <template v-slot:no-option>
      <q-item>
        <q-item-section class="text-grey">
          No results
        </q-item-section>
      </q-item>
    </template>
  </q-select>
  <q-input  v-model="this.$data.lvl" type="number">

  </q-input>
</template>

<script>
import { computed, ref } from 'vue'
import { useStore } from 'vuex'
import mobSelect from "../components/mobSelect.vue"

export default {
  data() {
    return {
      model: "",
      options: [],
      lvl : ref(""),
    }
  },
  props:{
    number:Number
  },
  setup() {
    const $store = useStore()
    let enchants = $store.getters["myStore/getEnchants"]
    
    const options = ref(enchants.map(item => item.name))

    const filterFn = (val, update) => {
      if (val === '') {
        update(() => {
          options.value = enchants.map(item => item.name)
        })
        return
      }
      update(() => {
        const needle = val.toLowerCase()
        options.value = enchants.map(item => item.name).filter(v => v.toLowerCase().indexOf(needle) > -1)
      })
    }



    return {
      options,
      filterFn,

    }
  },methods:{
    changecEnchant(value){
      console.log(67)
      this.$parent.setEnchants(value, this.$data.lvl , this.$props.number)
    }
  }
}
</script>
