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
          ref="itemInput"
        >
      </li>
    </ul>
  </div>
  
</template>

<script>
import {ref, reactive, watch, onMounted} from 'vue'
export default {
  setup() {
    const itemInput = ref([])
    const array = reactive([
	    {id: 1, title: ''},
      {id: 2, title: ''},
      {id: 3, title: ''}
    ])

    onMounted(() => {
      for (let i = 0; i < array.length; i++) {
        watching(array[i], i);
      }
    })

    const watching = (watchObj, idx) => {
      watch(() => watchObj,
          () => {
            for (let k = 0; k < array.length; k++) {
              itemInput.value[k].classList.remove('active')
            }
            itemInput.value[idx].classList.add('active')
          },
          {deep: true}
        )
    }
    
    
    return {
      array, itemInput, watching
    }
  } 
}
</script>

<style>
  .active {
    background-color: red;
  }
</style>
