<template>
  <q-page padding>
    <div class="row q-mb-lg">
      <q-input class="col" placeholder="Add new task"></q-input>
      <q-btn color=primary size=sm label=add/>
    </div>

    <div class="row">

      <q-list class="col" bordered separator>

       <q-item v-for= "task in tasks" v-bind:key = "task.id" label="task">

        <q-item-section avatar>
          <q-icon color="green" name="check" />
        </q-item-section>
      </q-item>  
    </q-list>

    </div>
    <div class="q-pa-md">
    <q-table
      title="Treats"
      :rows="rows"
      :columns="columns"
      row-key="name"
    />
  </div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'PageIndex',
  data(){
    return {
      tasks:[
        {id:1,task:'wake up'},
        {id:2,task:'take coffe'},
        {id:3,task:'brush'},
      
      ]
    }
    
  },
  setup () {
    return {
      columns,
      rows
    }
  }
})
//tabela
const columns = [
  {
    name: 'name',
    required: true,
    label: 'Registro de entrada',
    align: 'left',
    field: row => row.name,
    format: val => `${val}`,
    sortable: true
  },
  { name: 'pedidoItem', align: 'center', label: 'Pedido Item', field: 'pedidoItem', sortable: true },
  { name: 'origem', label: 'Retirar em', field: 'origem', sortable: true },
  { name: 'destino', label: 'Destino', field: 'destino' },
  { name: 'totalVolumes', label: 'Volumes a conferir', field: 'totalVolumes' },
  { name: 'volumesLidos', label: 'Volumes Lidos', field: 'volumesLidos' },
  { name: 'saldo', label: 'Faltam', field: 'saldo', sortable: true, sort: (a, b) => parseInt(a, totalVolumes) - parseInt(b, volumesLidos) },
  
]

const rows = [
  {
    name: '234345',
    pedidoItem: '23456789/001',
    origem: 'B1050101' ,
    destino: 'B1010101',
    totalVolumes: 30,
    volumesLidos: 30,
    saldo:'0'
    
  },
  {
    name: '234345',
    pedidoItem: '23456789/002'
  }]



//tabela
</script>

