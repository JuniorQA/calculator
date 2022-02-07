<template>
	<div class="btn-container">
		<ul><li><a href="#" class="btn" v-on:click="$emit('pushToInput', item)">{{buttonValue[index]}}</a></li></ul>
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
