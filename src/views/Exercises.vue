<template>
  <div class="about">
    <h1>Exercises from the book</h1>
    <Calcex/>
  </div>
</template>

<script>
import Calcex from "@/components/Calc_ex.vue"; 

export default {
  name: "exercises",
  components: {
    Calcex
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