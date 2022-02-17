<template>
	<div class="resbtn-container">
		<div><input type="button" value="Calculate" v-on:click="$emit('calcEvent', result)"></div>
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