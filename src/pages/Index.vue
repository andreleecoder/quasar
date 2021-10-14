<template>
  <q-page padding>
    <div class="row q-mb-lg">
      <q-input class="col" placeholder="Add new task"></q-input>
      <q-btn 
        color=primary
        size=sm
        label=add
      ></q-btn>
    </div>
    <div class="row">
      <q-list class="col" bordered separator>
       <q-item v-for= "task in tasks" :key = "task" label="task">
        <q-item-section avatar>
          <q-icon color="green" name="check" />
        </q-item-section>
      </q-item>  
    </q-list>
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'PageIndex',
  data(){
    return {
      tasks:['wake up','Brush teeth','shower','shower']
    }
    
  }
})
</script>
