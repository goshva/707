<template>
  <div class="hello">
    <div class="pie"></div>
    <hr>
    <button @click="toggleModalState">Open modal</button>
    <div v-if="modalOpen">
      <p>Hello, I'm a row graph.</p>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: 'GraphPad',
//
  setup () {
    const modalOpen = ref(false);
    const toggleModalState = () => {
      modalOpen.value = !modalOpen.value;
    };
    return {
      modalOpen,
      toggleModalState
    }
  },
//  
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.pie {
  width: 100px; height: 100px;
  border-radius: 50%;
  background: conic-gradient(#655 40%, yellowgreen 0);
  background: conic-gradient(deeppink 10%, #fb3 0, #fb3 15%, yellowgreen 15%);
}
</style>
