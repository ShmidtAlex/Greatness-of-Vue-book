

<template>
  <div class="about">
    <h1>Here is the page, where I will learn vue!</h1>
    <HelloVue msg="Hello, Your Magesty, Vue"/>
  </div>
</template>

<script>
import HelloVue from "@/components/HelloVue.vue";

export default {
  name: "about",
  components: {
  	HelloVue
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