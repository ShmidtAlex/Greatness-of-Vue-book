<template>
  <div class="about">
    <h1>Exercises from the book</h1>
    <Calcex/>
    <Elections/>
  </div>
</template>

<script>
import Calcex from "@/components/Calc_ex.vue"; 
import Elections from "@/components/MayorElections";

export default {
  name: "exercises",
  components: {
    Calcex,
    Elections
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