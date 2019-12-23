<template>
  <div class="someClass">{{story}}</div>
</template>
<script>
  export default {
    name: 'story',
    data: function() {
      return {
        story: 'some test text'
      }
    }
  }
</script>
