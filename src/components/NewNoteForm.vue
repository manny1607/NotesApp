<template>
	<form>
		<div class="form-group">
	    <label>Title</label>
	    <input v-model="title" class="form-control" type="text" placeholder="Title">
	    <label>Subtitle</label>
	    <input v-model="subtitle" class="form-control" type="text" placeholder="Subtitle">
	    <label>Write your note</label>
	    <textarea v-model="text" class="form-control" rows="3"></textarea>
	    <button @click.prevent="addNote" class="btn btn-success mt-2">Add Note</button>
	  </div>
  </form>
</template>

<script>
	export default{
		data () {
	    return {
    		title: '',
	      subtitle: '',
	      text: ''
	    }
	  },
	  props:['numNotes'],
	  methods:{
	  	addNote(){
	  		if (this.numNotes == 10) {
	  			return alert('Please delete a note')
	  		}
	  		let note = {
	  			id: this.numNotes + 1,
	  			title: this.title,
	  			subtitle: this.subtitle,
	  			text: this.text
	  		}
	  		this.$emit('addNote', note)
	  		this.emptyInputs();
	  	},
	  	emptyInputs(){
	      this.title = '';
	      this.subtitle = '';
	      this.text = '';
	    },
	  }
	}
</script>