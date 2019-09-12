<template>
	<div class="container">
		<h1>Введите 2 числа и выберите операцию.</h1> 
		<form class="form-inline">
			<input v-model.number="a" class="form-control">
			<select v-model="operator" class="form-control">
				<option>+</option>
				<option>-</option>
				<option>*</option>
				<option>/</option>
			</select>
			<input v-model.number="b" class="form-control">
			<button type="submit" @click.prevent="calculate" class="btn btn-primary"> 
				Вычислить
			</button> 
		</form>
		<h2>Результат: {{a}} {{operator}} {{b}} = {{c}}</h2>
		<pre>{{ $data }}</pre> </div><!--for displaying data as it is-->
</template>
<script>
	export default {
		name: "Calcex",
		data: function(){
			return {
				a: 1,
				b: 2,
				operator: '+'
			}
		},
		computed: {
			c: {
				//event.preventDefault();//аналогичным способом можно добавить превент-дефолт прямо на кнопку (см. DOM)
				get: function() {
					switch (this.operator) { 
						case '+':
							return this.c = this.a + this.b
							break; 
						case '-':
							return this.c = this.a - this.b
							break; 
						case '*':
							return this.c = this.a * this.b
							break; 
						case '/':
							return this.c = this.a / this.b
							break; 
					}
				},
				set: function(newValue) {
					return newValue;
				}
			}
		}
	}
</script>
<style></style>