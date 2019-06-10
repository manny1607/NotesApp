<template>
	<div class="row">
	  <div class="col-md-4" v-for="(note, index) in notes">
	    <note-card :note="note" @click.native="deleteNote(index)">
	    </note-card>
	  </div>
	</div>
</template>

<script>
	import NoteCard from './NoteCard.vue';
	export default{
	  props:['notes'],
	  methods:{
	  	deleteNote(index){
	  		this.$emit('noteDeleted', index)
	  	}
	  },
	  components:{
	  	NoteCard
	  }
	}
</script>

<style></style>