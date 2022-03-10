<template>
  <div class="container">
  <table class="table table-striped table-bordered">
      <thead>
          <tr>
              <th>id</th>
              <th>title</th>
              <th>rand</th>
          </tr>
      </thead>
      <tbody>
          <tr v-for="user in msg" :key="user.id">
              <td>{{user.id}} {{user.lastName}}</td>
              <td>{{user.title}}</td>
              <td>{{user.rand}}</td>
          </tr>
      </tbody>
  </table>

      <Graph :msg="msg"/>
  </div>    
</template>

<script>
//import { toRefs  } from 'vue'
import Graph from '@/components/Graph.vue'
export default {
  name: 'TableBoard',

  components: {
    Graph
  },
  props: {
    msg: Array
  },
  
}
</script>
<style scoped>
.container{
/*  display: flex;*/
}
</style>
