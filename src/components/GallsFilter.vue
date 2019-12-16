<template>
  <div class="GallsList">
    <h1>Some Gallian Sitizens</h1>
    <Galls />
  </div>
</template>
<script>
  import Vue from "vue";
  import   Galls  from './Galls';
  export default {
    name: 'GallsFilter',
    components: {
      Galls,
    },
    data: function() {
      return {
        
      }
    }

  }
</script>
