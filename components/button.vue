<template>
	<div class="btn-container">
		<a href="#" class="btn" v-on:click="$emit('pushToInput', item)">{{buttonValue[index]}}</a>
	</div>
</template>

<script>
	export default {
		name: 'calcButton',
		props : ['buttonValue','index','result', 'item'], 
		data(){
			return{
				
			}
		}
	}
</script>
