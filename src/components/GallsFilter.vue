<template>
  <div class="GallsList">
    <h1>Some Gallian Sitizens</h1>
    <button @click="changeSortOptions" class="btn">running sort option: {{option}}</button>
    <Galls :order="option" />
  </div>
</template>
<script>
  import   Galls  from './Galls';
  export default {
    name: 'GallsFilter',
    components: {
      Galls,
    },
    data: function() {
      return {
        sortOptions: null,
      }
    },
    computed: {
      option: function() {
        if (this.sortOptions !== null) {
          return this.sortOptions;
        } else {
          return "CHOOSE!"
        }
        
      }
    },
    methods: {
      changeSortOptions: function() {
        switch(this.sortOptions) {
          case null: this.sortOptions = "descending";
              break;
          case "descending": this.sortOptions = "ascending";
              break;
          default: this.sortOptions = null;
        }
      }
    }

  }
</script>
