<template>
	<div class="resbtn-container">
		<div><input class="calc-btn" type="button" value="Calculate" v-on:click="$emit('calcEvent', result)"></div>
	</div>
</template>

<script>
	export default {
		name: 'resBtn',
		props : ["result"], 
		data(){
			return{
				
			}
		}
	}
</script>