<template>
  <div class="home">
    <h1>Home</h1>
    <p ref="p">My name is {{ name }} and my age is {{ age }}</p>
    <button @click="handleClick">Click Me</button>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "Home",
  setup() {
    
    console.log(this);

    const p = ref(null);

    let name = "Ros";
    let age = 30;

    const handleClick = () => {
      console.log(p.value);
      p.value.classList.add('test')
    };

    return {
      name,
      age,
      handleClick,
      p,
    };
  },
};
</script>
