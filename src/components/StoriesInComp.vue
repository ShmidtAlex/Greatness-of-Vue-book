<template>
  <div class="storyTailes">
    <h1>Let's listen to some stories!</h1>
    <ul class="list-group">
      <story v-for="(story, index) in stories" :key="index" :story="story"></story>
    </ul>
  </div>
</template>
<script>
  // import Vue from 'vue';
  import story from "./story";
  export default {
    name: 'StoriesInComp',
    components: {
      story
    },
    data: function(){
      return {
        stories: [
          {
            plot: 'My horse is incredible',
            writer: 'Mr. Wibble'
          },
          {
            plot: 'Narwhals created barbecue',
            writer: 'Mr. Wibble'
          },
          {
            plot: "Dark side of Power is stronger",
            writer: "Dart Weider" 
          },
          {
            plot: "It's not so simple, enter to Mordor",
            writer: "Boromir"
          }
        ]
      }
    },
    computed: {

    },
    methods: {

    }
  }
</script>