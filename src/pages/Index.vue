<template>
  <q-page padding>
    <div class="row q-mb-lg">
      <q-input v-model="newTask" class="col" placeholder="Add new task"></q-input>
      <q-btn 
        color=primary
        size=sm
        label=add
        @click="addTask"
      ></q-btn>
    </div>
     <div class="row">
      <q-list class="col" bordered separator>
        <q-list-header>Tasks</q-list-header>
       <q-item v-for= "(task, index) in tasks" v-bind:key = "index" > 
          <q-item-section>
          {{task}}  
          </q-item-section>  
        <q-item-section avatar>
          <q-icon @click="moveToDone(index)" color="green" name="check"/>
        </q-item-section>   
     </q-item>  
    </q-list>
    </div>

     <div class="row">
      <q-list class="col" bordered separator>
        <q-list-header>Done</q-list-header>
       <q-item v-for= "(task, index) in done" v-bind:key = "index" > 
          <q-item-section>
          {{task}}  
          </q-item-section> 
          <q-item-section avatar>
          <q-icon @click="deleteTask(index)" color="red" name="close" />
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
      tasks:[],
      done:[],
      newTask:''    
    }
    
  },
  methods:{
  addTask(){
    this.tasks.push(this.newTask)
    this.newTask=''
  },
  moveToDone(index){
    this.done.push(this.tasks[index])
    this.tasks.splice(index, 1)
  },
   deleteTask(index){
     this.$q.dialog({
       title:'confirm',
       message:'Really want to delete?',
       ok:'Yes',
       cancel:'No'
     }).then(() => {
       this.done.splice(index, 1)
       this.$q.notify('Deleted')
     }).catch(() => {
     
     })
   }
  }
  })
  
</script>
