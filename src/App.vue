<template>
  <div>
    <ul>
      <li 
        v-for="item in array"
        :key="item.id"
        
      >
        <input
          type="text" 
          v-model="item.title"
          @input="index = item.id"
          :class="{active: index == item.id}"
        >
      </li>
    </ul>
  </div>
  
</template>

<script>
import {ref, reactive} from 'vue'
export default {
  setup() {
    const array = reactive([
	    {id: 1, title: ''},
      {id: 2, title: ''},
      {id: 3, title: ''}
    ])

    const index = ref()

    return {
      array, index
    }
  } 
}
</script>

<style>
  .active {
    background-color: red;
  }
</style>
