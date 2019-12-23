<template>
  <div class="about">
    <h1>Exercises from the book part 3</h1>
    <GallsFilter/>
    <StoriesInComp/>
  </div>
</template>

<script>
// @ is an alias to /src
import GallsFilter from "@/components/GallsFilter.vue";
import StoriesInComp from "@/components/StoriesInComp.vue";
export default {
  name: "exercises_3",
  components: {
    GallsFilter,
    StoriesInComp,
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