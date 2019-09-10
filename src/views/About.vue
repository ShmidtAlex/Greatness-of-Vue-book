

<template>
  <div class="about">
    <h1>Here is the page, where I will learn vue!</h1>
    <HelloVue msg="Hello, Your Magesty, Vue"/>
    <Calculator />
    <!-- <Calcex/> -->
  </div>
</template>

<script>
import HelloVue from "@/components/HelloVue.vue";
import Calculator from "@/components/Calculator.vue";
// import Calcex from "@/components/Calc_ex.vue"; 

export default {
  name: "about",
  components: {
  	HelloVue,
    Calculator,
    // Calcex
  }
};
</script>
<style>
	.about {
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		align-items: center; 
		background-color: rgba(220, 220, 200, 0.5);
	}
</style>