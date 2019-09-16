<template>
  <div class="about">
    <h1>Exercises from the book part Two</h1>
    <CustomFilter/>
  </div>
</template>

<script>
// @ is an alias to /src
import CustomFilter from "@/components/CustomFilter.vue";

export default {
  name: "exercises2",
  components: {
    CustomFilter,
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