<template>
	<div class="card mb-4">
	  <div class="card-body">
	  	<slot name="title">
	  		<!-- <h5 class="card-title">Card title</h5> -->
	  	</slot>
	  	<slot name="subtitle">
	  		<!-- <h6 class="card-subtitle mb-2 text-muted">Card subtitle</h6> -->
	  	</slot>
	  	<slot name="text">
	  		<!-- <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p> -->
	  	</slot>
	  </div>
	</div>
</template>

<script>
	export default{
		props: ['noteId']
	}
</script>

<style>
	.card{
		cursor: pointer;
	}
</style>