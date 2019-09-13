<template>
	<div class="container">
		<h1>Mayor Elections</h1>
		<div class="candidates_block" >
			<table  class="candidate">
				<tr>
					<th>candidate name</th>
					<th>candidate age</th>
					<th>candidate profession</th>
					<th>candidate votes</th>
					<th>action!</th>
				</tr>
				<tr v-for="(candidate, indexItm) in candidates" :key="indexItm">
					<td class="name">{{candidate.name}}</td>
					<td class="age">{{candidate.age}}</td>
					<td class="profession">{{candidate.profession}}</td>
					<td class="votes">{{candidate.votes}}</td>
					<td><button @click="candidate.votes++" class="vote">vote!</button></td>
				</tr>
			</table>
		</div>
		<div class="runningMayor">
			<!-- think, how to prevent initial candidate's name -->
			<h2>Our mayor now is: {{ findRunningMayor[0].name }}</h2>
		</div>
		<div class="reset">
			<button @click="reset" class="btn btn-primary">start election again!</button> 
		</div>
	</div>
</template>
<script>
	export default {
		name: "Elections",
		data: function() {
			return {
				candidates: [
					{ name: "Harry Busy", age: 60, votes: 0, profession: "actor" },
					{ name: "Donald Trump", age: 70, votes: 0, profession: "businessman" },
					{ name: "Damian Porque", age: 35, votes: 0, profession: "phylosopher" },
					{ name: "Dmitry Nagiev", age: 55, votes: 0, profession: "showman" },
					{ name: "Daniel Spark", age: 49, votes: 0, profession: "military surgeon" },
					{ name: "Terry Duval", age: 60, votes: 0, profession: "artist" },
					{ name: "Max McConnohew", age: 61, votes: 0, profession: "farmer" },
				],
			}
		},
		computed: {
			changedVotes: function() {
				let self = this;
				return self.candidates.votes;
			},
			findRunningMayor: function() {
        /*it's not very convinient, that candidates move up when their voter numbers grows up
          user has to search his candidate button again and again while voting continuing. For
          avoiding it we do not sort the whole candidate array, we create new array and push our
          objects into it. That won't possible to do that by assigning whole array to new array.
        */
				let ourMayorIs2 = [];
        this.candidates.forEach(function(element) {
          ourMayorIs2.push(element);
        });
				ourMayorIs2.sort(function(a,b){
					return b.votes - a.votes;
				});
				return ourMayorIs2;
			}
		},
		methods: {
			reset: function() {
				// this.candidates.forEach(function(element){
				// 	element.votes = 0;
				// })
				//or use more convenient map method:
				this.candidates = this.candidates.map(function(candidate) {
					candidate.votes = 0;
					return candidate
				})
			}
		}
	}
</script>
<style>
	.container {
		padding-bottom: 50px;
	}
	.candidates_block {
		width: 100%;
	}

	.candidate {
		width:100%;
		border: 1px double gray;
	}
	th {
		border:1px solid gray;
		height: 37px;
		text-align: center;
	}
	td {
		border: 1px solid gray;
		overflow: hidden;
		height: 37px;
	}
</style>