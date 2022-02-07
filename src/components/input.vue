<template>
	<div class="input-container">
		<input type="text" v-model="result">
	</div>
</template>

<script>
	export default {
		name: 'calcInput',
		props : ["result", 'buttonValue'], 
		data(){
			return{
				
			}
		}
	}
</script>