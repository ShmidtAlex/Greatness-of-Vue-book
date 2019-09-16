<template>
	<div class="container">
		<h3>Alex Stories</h3>
		<ul class="list-group">
			<li v-for="(story, index) in storiesBy('Alex')" :key="index" class="list-group-item">
				{{story.writer}} said: {{story.plot}} 
			</li>	
		</ul>
		
		<h3>John Stories</h3>
    
		<ul class="list-group">
      <!-- yes, we can use new array, which is the result of function storiesBy -->
			<li v-for="(story, index) in storiesBy('John')" :key="index" class="list-group-item">
				{{story.writer}} said: {{story.plot}}
			</li>
		</ul>	
    <div class="famous_stories">
      <h3>Let's listen famouse stories! (number of: {{ famous.length }})</h3>
      <ul class="list-group">
        <li class="list-group-item" v-for="(story, index) in famous" :key="index">
          {{ story.writer }} said "{{ story.plot }}" and got {{ story.upvotes}} votes
        </li>
      </ul>
    </div>
    <pre>{{$data}}</pre>
    <div class="form-group">
      <label for="query">Type what are you searching for</label>
      <input v-model="query" class="form-control">
    </div>
    <ul class="list-group">
      <li v-for="(story, index) in search" :key="index" class="list-group-item">
        {{ story.writer }} сказал "{{ story.plot }}"
      </li> 
    </ul>
    <h1>Ordered stories</h1>
    <ul class="list-group">
      <li class="list-group-item" v-for="(story, index) in orderSearch" :key="index">
        {{ story.writer }} told "{{ story.plot }}" and gave {{ story.upvotes }} votes
      </li>
    </ul>
    <button class="btn btn-primary" @click="order = order*-1">in reverse order</button>
	</div>
</template>
<script>
	export default {
		name: "Stories",
		data: function() {
			return {
				stories: [
					{
						plot: "today I have broken my car!",
						writer: 'Alex',
            upvotes: 28,
					},
          {
            plot: "yesterday someone have thiefed my bag",
            writer: "John",
            upvotes: 8,
          },
          {
            plot: "sombody has eaten my chockolate",
            writer: "John",
            upvotes: 32,
          },
          {
            plot: "I've eaten sombody's chockolate",
            writer: "Alex",
            upvotes: 31,
          },
				],
        query: ' ',
        order: -1,
			}
		},
    methods: {
      //for searching in global vocabulary according to part of speech, topic and so on
      storiesBy: function(writer) {
        return this.stories.filter(function(story){
          return story.writer === writer;
        })
      },
    }, 
    computed: {
      //for filter words, which were already studied
      famous: function() {
        return this.stories.filter(function(item) {
          return item.upvotes > 25;
        });
      },
      search: function() {
        //for searching in the personal list of words
        let query = this.query;
        return this.stories.filter(function(story){
          return story.plot.includes(query);
        })
      },
      orderSearch: function() {
        let self = this;
        return this.stories.sort(function(a, b){
          return (a.upvotes - b.upvotes) * self.order;
        })
      }
    }
	}
</script>
<style></style>