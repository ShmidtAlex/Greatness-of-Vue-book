<template>
  <div class="about">
    <h1>Exercises from the book part 3</h1>
    <GallsFilter/>
  </div>
</template>

<script>
// @ is an alias to /src
import GallsFilter from "@/components/GallsFilter.vue";
// import Galls from '../Galls';

export default {
  name: "exercises_3",
  components: {
    GallsFilter,
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