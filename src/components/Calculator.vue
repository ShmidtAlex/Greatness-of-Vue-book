<template>
	<div class="container">
		<div class="screen_wrapper">
			<div class="screen_wrapper__up_block">
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
				<div class="screen_wrapper__up_block__tumbler">
					<div @click="isOn = !isOn" class="tumbler__area" >
						<span :class="{ active: !isOn }">off</span>
						<div class="tumbler__button" :class="{ on : isOn }"></div>
						<span :class="{ active: isOn }">on</span>
					</div>
					
				</div>
			</div>
				
			<div class="screen_wrapper__resuls">
				<div class="screen_wrapper__result__left">
					<div class="screen_wrapper__mathAction">{{runningOperator}}</div>
					<div class="expression">{{generalExpression}}</div>
				</div>
				<div class="screen_wrapper__result__right">
					{{screenValue}}
				</div>
			</div>
		</div>
		<div class="number_wrapper">
			<div class="number_wrapper__form"><!--I'm not sure, that tag "form" is
				necessary in this case-->
				<div class="number_wrapper__numbers">
					<input @click="addToScreen" type="button" class="number_wrapper__number" value=7>
					<input @click="addToScreen" type="button" class="number_wrapper__number" value=8>
					<input @click="addToScreen" type="button" class="number_wrapper__number" value=9>
					<input @click="addToScreen" type="button" class="number_wrapper__number" value=4>
					<input @click="addToScreen" type="button" class="number_wrapper__number" value=5>
					<input @click="addToScreen" type="button" class="number_wrapper__number" value=6>
					<input @click="addToScreen" type="button" class="number_wrapper__number" value=1>
					<input @click="addToScreen" type="button" class="number_wrapper__number" value=2>
					<input  @click="addToScreen"type="button" class="number_wrapper__number" value=3>
					<input @click="addToScreen" type="button" class="number_wrapper__number" value=0>
				</div>
				<div class="number_wrapper__math-signs">
					<input @click="clear" @keyup.127="clear" type="button" class="number_wrapper__sign" value="C">
					<input @click="plus" @keyup.107="plus" type="button" class="number_wrapper__sign" value="+">
					<input @click="minus" @keyup.109="minus" type="button" class="number_wrapper__sign" value="-">
					<input @click="multiply" @keyup.106="multiply" type="button" class="number_wrapper__sign" value="*">
					<input @click="devide" @keyup.191="devide" type="button" class="number_wrapper__sign" value="/">
					<!-- @keyup.13="equalTo" is the same as @keyup.enter="equalTo" -->
					<input @click="equalTo" @keyup.enter="equalTo" type="button" class="number_wrapper__sign" value="=">
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
				initialValue: '0',
				runningOperator: null,
				screenValue: '0',
				runningValue: '',
				result: null,
				isOn: false,
				accomodationString: '',/*add all results and acrions to the small string
				on the top of the string*/
			}
		},
		computed: {
			generalExpression: function() {
				//this have to display whole operations chain
				if (this.initialValue !== '0') {
					this.accomodationString = this.initialValue;
				} else if (this.initialValue !== '0' && this.runningOperator !== null) {
					this.accomodationString += this.runningOperator;
				} else if (this.runningValue !== '') {
					this.accomodationString += this.runningValue;
				}
				return this.accomodationString;
			}
		},
		methods: {
			
			clear: function() {
				if (this.isOn) {
					this.initialValue = '0';
					this.runningOperator = null;
					this.screenValue = '0';
				}
			},
			plus: function() {
				//можно переделать, через   v-bind прямо в теге?
				if (this.isOn) {
					this.runningOperator = "+";	
				}
			},
			multiply: function() {
				if (this.isOn) {
					this.runningOperator = "*";		
				}
			},
			minus: function() {
				if (this.isOn) {
					this.runningOperator = "-";
				}
			},
			devide: function() {
				if (this.isOn) {
					this.runningOperator = "/";
				}
			},
			addToScreen: function() {
				if (this.isOn) {
					if (this.initialValue === '0') {
						if(!event.key) {
							this.initialValue = event.target.value;
						} else {
							this.initialValue = event.key;
						}
						this.screenValue = this.initialValue;
					} else if (this.initialValue !== '0' && !this.runningOperator) {
						if(!event.key) {
							this.initialValue += event.target.value;
						} else {
							this.initialValue += event.key;
						}
						this.screenValue = this.initialValue;
					} else {
						if (this.runningValue === '') {
							if(!event.key) {
								this.runningValue = event.target.value;
							} else {
								this.runningValue = event.key;
							}
							// this.screenValue = this.runningValue;
						} else {
							if(!event.key) {
								this.runningValue += event.target.value;
							} else {
								this.runningValue += event.key;
							}
						}
						this.screenValue = this.runningValue;
					}
				} else {
					return;
				}
				
			},
			equalTo: function() {
				switch (this.runningOperator) {
					case this.runningOperator = "+": 
						if (this.initialValue !== '0') {
						 this.screenValue = Number(this.initialValue) + Number(this.runningValue);
						 this.initialValue = this.screenValue;
						 this.runningValue = '';
						}
						break;
					case this.runningOperator = "*":
						if (this.initialValue !== '0') {
						 this.screenValue = Number(this.initialValue) * Number(this.runningValue);
						  this.initialValue = this.screenValue;
						  this.runningValue = '';
						}
						break;
					case this.runningOperator = "-":
						if (this.initialValue !== '0') {
						 this.screenValue = Number(this.initialValue) - Number(this.runningValue);
						 this.initialValue = this.screenValue;
						 this.runningValue = '';
						}
						break;
					case this.runningOperator = "/":
						if (this.initialValue !== '0') {
						 this.screenValue = Number(this.initialValue) / Number(this.runningValue);
						 this.initialValue = this.screenValue;
						 this.runningValue = '';
						}
						break;		
					default: return;
				}				 
			}
		},
		mounted() {
			if (this.isOn) {
				//чтобы назначить вызов функционала соответствующим клавишам, делаем это в mounted
				var self = this;
			    window.addEventListener('keyup', function(event) {
			      if (event.keyCode === 13) { 
			        self.equalTo();
			      }
			      if (event.keyCode === 191) { 
			        self.devide();
			      }
			      if (event.shiftKey && event.keyCode === 104) { 
			        self.multiply();
			      }
			      if (event.shiftKey && event.keyCode === 187) { 
			      	self.plus();
			      }
			      if (event.shiftKey && event.keyCode === 189) { 
			        self.minus();
			      }
			      if (event.keyCode === 46) { 
			      	console.log("clear");
			        self.clear();
			      }
			      //add here all numbers keys as below

			      if (event.keyCode === 49) { 
			        self.addToScreen();
			      }
			      if (event.keyCode === 50) { 
			        self.addToScreen();
			      }
			      if (event.keyCode === 51) { 
			        self.addToScreen();
			      }
			      if (event.keyCode === 52) { 
			        self.addToScreen();
			      }
			      if (event.keyCode === 53) { 
			        self.addToScreen();
			      }
			      if (event.keyCode === 54) { 
			        self.addToScreen();
			      }
			      if (event.keyCode === 55) { 
			        self.addToScreen();
			      }
			      if (event.keyCode === 56) { 
			        self.addToScreen();
			      }
			      if (event.keyCode === 57) { 
			        self.addToScreen();
			      }
			      if (event.keyCode === 48) { 
			        self.addToScreen();
			      }

		    	});
			}
	    },
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
	.screen_wrapper__up_block {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		height: 50%;
	}
	.screen_wrapper__solar-battery {
		width: 40%;
		height: 70%;
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
	.screen_wrapper__up_block__tumbler {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		width: 20%;
		height: 70%;
		border: 1px solid gray;
		background-color:rgba(50,50,50, .6);
		margin-right: 10px; 
		padding: 0 2px;
	}
	.tumbler__area {
	  position: relative;
	  width: 97%;
	  height: 80%;
		background-color: lightgray;
		border-radius: 20px;
		border: 1px solid darkgray;
		display: flex;
		flex-direction: row;
		justify-content: space-around;
		align-items: center;
	}
	.on {
		/*justify-content: flex-start;*/
		margin-left: 35px !important;
	}
	.tumbler__button {
		position: absolute;
		top:0px;
		left:0px;
		background-color: rgba(50,50,50, .6);
		height: 94%;
		width: 56%;
		border-radius: 20px;
		border: 1px solid gray;
		margin: 1px 1px;
		transition: all 1s ease-in-out;
	}
	.active {
		color: red;
		transition: all 1s ease-in-out;
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
		justify-content: space-between;
		align-items: center;
		padding: 2px 10px;
		font-weight: 800;
		font-size: 30px;
	}
	.screen_wrapper__result__left {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		align-items: flex-start;
		height: 100%;
	}
	.expression {
		overflow: hidden;
		font-size: 10px;
		font-weight: 400;
		height: 40%;
		width: 100%;
		/*background-color: white;*/
	}
	.screen_wrapper__mathAction {
		width: 20px;
		height: 20px;
		background-color: darkgray;
		color:white;
		align-self: flex-start;
		font-size: 15px;
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