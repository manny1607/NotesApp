<template>
	<div class="progress">
	  <div class="progress-bar" role="progressbar" :style="{width: numNotes+'0%'}">{{numNotes}}/10</div>
	</div>
</template>

<script>
	export default{
		props:['numNotes']
	}
</script>