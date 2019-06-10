<template>
	<div class="card mb-4">
	  <div class="card-body">
	  		<h5 class="card-title">{{note.title}}</h5>
	  		<h6 class="card-subtitle mb-2 text-muted">{{note.subtitle}}</h6>
	  		<p class="card-text">{{note.text}}</p>
	  	</slot>
	  </div>
	</div>
</template>

<script>
	export default{
		props: ['note']
	}
</script>

<style>
	.card{
		cursor: pointer;
	}
</style>