<template>
	<div class="container">
		<div class="screen_wrapper">
			<div class="screen_wrapper__solar-battery">
				<div class="screen_wrapper__battery_item"></div>
				<div class="screen_wrapper__battery_item"></div>
				<div class="screen_wrapper__battery_item"></div>
				<div class="screen_wrapper__battery_item"></div>
				<div class="screen_wrapper__battery_item"></div>
				<div class="screen_wrapper__battery_item"></div>
				<div class="screen_wrapper__battery_item"></div>
				<div class="screen_wrapper__battery_item"></div>
			</div>
			<div class="screen_wrapper__resuls">{{initialValue}}</div>
		</div>
		<div class="number_wrapper">
			<div class="number_wrapper__form"><!--I'm not sure, that tag "form" is
				necessary in this case-->
				<div class="number_wrapper__numbers">
					<input type="button" class="number_wrapper__number" value=1>
					<input type="button" class="number_wrapper__number" value=2>
					<input type="button" class="number_wrapper__number" value=3>
					<input type="button" class="number_wrapper__number" value=4>
					<input type="button" class="number_wrapper__number" value=5>
					<input type="button" class="number_wrapper__number" value=6>
					<input type="button" class="number_wrapper__number" value=7>
					<input type="button" class="number_wrapper__number" value=8>
					<input type="button" class="number_wrapper__number" value=9>
					<input type="button" class="number_wrapper__number" value=0>
				</div>
				<div class="number_wrapper__math-signs">
					<input type="button" class="number_wrapper__sign" value="C">
					<input type="button" class="number_wrapper__sign" value="+">
					<input type="button" class="number_wrapper__sign" value="-">
					<input type="button" class="number_wrapper__sign" value="*">
					<input type="button" class="number_wrapper__sign" value="/">
					<input type="button" class="number_wrapper__sign" value="=">
				</div>
			</div>
			
		</div>
	</div>
</template>
<script>
	export default {
		name: "Calculator",
		data: function() {
			return {
				initialValue: 0,
				runningOperator: "+",
			}
		}
	}
</script>
<style scoped>
	.container {
		background-color: rgba(0,0,0, .6);
		width: 500px;
		height: 700px;
		border: 1px solid rgba(0,0,0, .6);
		border-radius: 6px;
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		align-items: center;
	}
	.screen_wrapper {
		height: 20%;
		width: 97%;
		border: 1px solid rgba(0,0,0, .6);
		border-radius: 6px;
		background-color: lightgray;
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		align-items: space-around;
	}
	.screen_wrapper__solar-battery {
		width: 40%;
		height: 40%;
		margin:10px;
		background-color: gray;
		border: 1px solid black;
		/*align-self: flex-end;*/
		justify-self: flex-start;
		border-radius: 6px;
		display: flex;
		flex-direction: row;
		justify-content: space-around;
		align-items: center;
	}
	.screen_wrapper__battery_item {
		height: 97%;
		width: 11%;
		background-color: black;

	}
	.screen_wrapper__resuls {
		width: 98%;
		height: 50%;
		align-self: center;
		margin:10px;
		border: 1px solid rgba(30,30,30, .6);
		background-color: rgba(240,240,240, .6);
		display: flex;
		flex-direction: row;
		justify-content: flex-end;
		align-items: center;
		padding: 10px;
		font-weight: 800;
		font-size: 30px;
	}

	.number_wrapper {
		height: 70%;
		width:97%;
		background-color: rgba(100,100,100, .6);
		border: 1px solid whitesmoke;
		border-radius: 6px;
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;

	}
	.number_wrapper__form {
		border: 1px solid whitesmoke;
		width: 97%;
		height: 97%;
		display: flex;
		flex-direction: row;
		justify-content: space-around;
		align-items: center;
		border-radius: 6px;
	}
 	.number_wrapper__numbers {
		width:70%;
		height: 98%;
		border: 1px solid rgba(0,0,0, .6);
		background-color: rgba(50,50,50, .6);
		border-radius: 6px;
		display: flex;
		flex-direction: row;
		justify-content: space-around;
		align-items: center;
		flex-wrap: wrap;
		padding: 15px 0;
	}
	.number_wrapper__number {
		width: 80px;
		height: 80px;
		font-size: 30px;
		font-weight: 800;
		border-radius: 6px;
	}
	.number_wrapper__math-signs {
		width: 25%;
		height: 98%;
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		align-items: center;
		border: 1px solid rgba(0,0,0, .6);
		background-color: rgba(50,50,50, .6);
		border-radius: 6px;
		padding: 25px 0;
	}
	.number_wrapper__sign {
		width:80px;
		height: 60px;
		font-size: 30px;
		font-weight: 800;
		border-radius: 6px;

	}
</style>