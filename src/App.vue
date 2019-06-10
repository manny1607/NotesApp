<template>
  <div id="app">
    <div class="container">
      <h1>Notes app</h1>
      <progress-bar :numNotes="notes.length"></progress-bar>
      <div class="row mt-3">
        <div class="col-md-6 offset-md-3">
          <div class="form-group">
            <label>Title</label>
            <input class="form-control" type="text" placeholder="Title">
            <label>Subtitle</label>
            <input class="form-control" type="text" placeholder="Subtitle">
            <label>Write your note</label>
            <textarea class="form-control" rows="3"></textarea>
            <button @click="addNote()" class="btn btn-success">Add Note</button>
          </div>
        </div>
      </div>

      <div class="row">
        <div class="col-md-4" :key="note.id" v-for='note in notes'>
          <note-card></note-card>
        </div>
      </div>
      
    </div>
  </div>
</template>

<script>
import ProgressBar from './components/ProgressBar.vue';
import NoteCard from './components/NoteCard.vue';
export default {
  name: 'app',
  data () {
    return {
      notes: [
        {id:1, title:'Card Title', subtitle:'Card subtitle', text:'Some quick example text to build on the card title and make up the bulk of the card\'s content.'}
      ]
    }
  },
  methods:{
    addNote(){
      var noteId = this.notes.length + 1; 
      this.notes.push({
        id:noteId,
        title:'Another Card',
        subtitle: 'Another sub',
        text: 'Blabblablabalbalfaijsdoicwaiopoisñoixñvnpxufxefxhoiryeaafnoxfyoaifapsc'
      })
      console.log(this.notes)
    }
  },
  components:{
    ProgressBar,
    NoteCard
  }
}
</script>

<style>
body{
  margin-top: 20px;
}
</style>
