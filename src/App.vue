<template>
  <div id="app">
    <div class="container">
      <h1>Beautiful Notes App</h1>
      <progress-bar :numNotes="notes.length"></progress-bar>
      <div class="row mt-3">
        <div class="col-md-6 offset-md-3">
          <new-note-form @addNote="newNote" :numNotes="notes.length"></new-note-form>
        </div>
      </div>

      <div class="alert alert-danger text-center" v-if="notes.length == 10">
        You can't add more notes
      </div>

      <note-grid :notes="notes" @noteDeleted="deleteNote"></note-grid>
      
    </div>
  </div>
</template>

<script>
import ProgressBar from './components/ProgressBar.vue';
import NewNoteForm from './components/NewNoteForm.vue';
import NoteGrid from './components/NoteGrid.vue';
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
    newNote(note){
      this.notes.push(note)
      console.log(this.notes)
    },
    deleteNote(index){
      this.notes.splice(index,1);
    }
  },
  components:{
    ProgressBar,
    NewNoteForm,
    NoteGrid
  }
}
</script>

<style>
body{
  margin-top: 20px;
}
</style>
