
<script>
export default {
  name: "HelloVue",
  props: {
    msg: String
  },
  data: function() {
    return {
      parents: null,
      stories: 
      {
        author: "Arthur",
        plott: "I've won GreenCard!",
        upwotes: 3

      }
    }
  },
  methods: {
    clearParentsField: function() {
      this.parents = null;
    },
    upwote: function() {
      this.stories.upwotes++;
    }
  }
};
</script>
<template>
   <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="word_card">
      <textarea v-model="parents" name="" id="" cols="30" rows="10"></textarea>
      <div class="parentsName">My parents' name are {{ parents }}</div>

      <button v-show="parents" class="delete" @click='clearParentsField'>delete</button>
      <!-- Important: use v-show, when your elements are going to switch often 
          otherwise use v-if (becouse of it has high coast of switching but fast displaying) -->

    </div>
    <h3>V-for demo</h3>
    <ul class="list-group"><li v-for="i in 5"class="list-group-item">{{i}} * 4  = {{i*4}}</li></ul> 
    <h3>Success stories</h3>
    <div class="true-story">
      <ul class="list-group">
        <li v-for="(story, key, storyIndex) in stories" :key="storyIndex" class="list-group-item">
         {{storyIndex+1}} : {{key}} : {{story}} {{story.upwotes}}
        <!-- <span class="addedSpan">key = {{key}}</span> -->
      </li>
      <button class="btn btn-small btn-primary" @click="upwote">Upwote</button>
      </ul>
    </div>
  </div>
</template>
<style>
  .word_card {
    height: 300px;
    width: 400px;
    background-color: lightgreen;
    border: 3px solid green;
    border-radius: 5px;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center; 
  }
  .delete {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    height: 30px;
    width: 30%;
    font-size: 14px;
    font-weight: bold;
    background-color: green;
    color: coral;
  }
  .addedSpan {
    background-color: lightblue;
  }
 </style>