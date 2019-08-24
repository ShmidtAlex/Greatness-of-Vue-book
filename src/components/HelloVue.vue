<template>
	 <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="word_card"></div>
  </div>
</template>
<script>
export default {
  name: "HelloVue",
  props: {
    msg: String
  }
};
</script>
<style>
  .word_card {
    height: 300px;
    width: 400px;
    background-color: lightgreen;
    border: 3px solid green;
    border-radius: 5px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: stretch; 
  }
</style>