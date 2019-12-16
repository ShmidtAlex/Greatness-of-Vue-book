<template>
  <div class="about">
     <h4>famous galls:</h4>
   <ul class="gallsList">
     <li class="eachGall" v-for="(gall, index) in galls">Name: {{gall.name}}, age: {{gall.age}}</li>
   </ul>
   <button class="btn" @click="showOldGalls"> Show Old Guard only! </button>
   <div class="listContainer" v-if="isOldShown">
     <h4>old galls:</h4>
     <ul class="oldGallsList">
       <li class="eachGall" v-for="(gall, index) in galls"> {{ gall | oldGuy }} </li>
     </ul>
   </div>
   
  </div>
</template>

<script>
  import Vue from 'vue';
  Vue.filter('oldGuy', function(gall){
    if (gall.age > 65)
    return `Name: ${gall.name}, age: ${gall.age}`;
  })
  export default {
    name: 'Galls',
    data: function(){
      return {
          galls: [
            {
              name: "Asterics", age: 32
            },
            {
              name: "Obelics", age: 33
            },
            {
              name: "Julius Cezar", age: 66
            },
            {
              name: "Magestics", age: 82
            },
            {
              name: "Veteranics", age: 103
            },
          ],
          isOldShown: false
      }
    },
    mounted() {
      this.sortByAge();
    },
    methods: {
      sortByAge:function() {
          this.galls.sort(function(a, b) {
            return b.age - a.age;
          });
      },
      showOldGalls: function() {
        this.isOldShown = true;
      }
    }
  };
</script>
<style>
  ul {
    list-style-type: none;
  }
</style>