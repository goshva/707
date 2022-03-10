<template>
  <main>
    <div class="bd-example">
      <div class="input-group mb-3">
        <div class="input-group-prepend">
          <span class="input-group-text" id="basic-addon1">Кол-во</span>
        </div>
        <input v-model="amount" type="text" class="form-control" :placeholder="dataTable.length" aria-label="Username" aria-describedby="basic-addon1">
        <div class="input-group-prepend">
          <span class="input-group-text" id="basic-addon1">Кол-во на странице</span>
        </div>
        <input v-model="amountPage" type="text" class="form-control" :placeholder="dataTable.length" aria-label="Username" aria-describedby="basic-addon1">        
        <div class="input-group-prepend">
          <span class="input-group-text" id="basic-addon1">Фильтр</span>
        </div>
        <input v-model="filterArr" type="text" class="form-control" :placeholder="dataTable.length" aria-label="Username" aria-describedby="basic-addon1">  
      </div>
      <button v-on:click="greet()" type="button" class="btn btn-primary">Apply</button>
      <button v-on:click="zeroState()" type="button" class="btn btn-warning">Reset</button>

    </div>  
    <button v-on:click="pag(-1)" type="button" class="btn">◀️</button>
    <button v-on:click="pag(1)" type="button" class="btn">▶️</button>
    <TableBoard :msg="dataTable"/>
  </main>ываыва
</template>

<script>
import { reactive } from "vue";

import TableBoard from './components/TableBoard.vue'

function initialData () {
  return [
    {"id": 1, "title": "name1", "rand": "apple"},
    {"id": 2, "title": "name2", "rand": "tomato"},
    {"id": 3, "title": "name3", "rand": "potato"},
    {"id": 4, "title": "name4", "rand": "orange"}
    ]
}
export default {
  name: 'App',
  setup () {
    const dataTable  = reactive(initialData());
    const amount = dataTable.length
    const amountPage = 3;
    const filterArr = [];
    return {
      dataTable,
      amount,
      amountPage,
      filterArr,
      
    }
  },
  components: {
    TableBoard
  },
//
methods: {
    greet: function () {
      //this.dataTable.pop();
      this.dataSlicer()
      console.log(this.dataTable)
    },
    zeroState: function () {
      location.reload();

    },
    dataSlicer: function(){
      this.dataTable.splice(initialData().length - this.amount)
    }    
  }
//
}
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
