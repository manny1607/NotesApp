<template>
  <div id="app">
    <div class="container">
      <h1>Beautiful Notes App</h1>
      <progress-bar :numNotes="notes.length"></progress-bar>
      <div class="row mt-3">
        <div class="col-md-6 offset-md-3">
          <div class="form-group">
            <label>Title</label>
            <input v-model="titleInput" class="form-control" type="text" placeholder="Title">
            <label>Subtitle</label>
            <input v-model="subtitleInput" class="form-control" type="text" placeholder="Subtitle">
            <label>Write your note</label>
            <textarea v-model="textInput" class="form-control" rows="3"></textarea>
            <button @click="addNote()" class="btn btn-success mt-2">Add Note</button>
          </div>
        </div>
      </div>

      <div class="alert alert-danger" v-if="notes.length == 10">
        You can't add more notes
      </div>

      <div class="row">
        <div class="col-md-4" :key="note.id" v-for='note in notes'>
          <note-card :noteId="note.id" @click.native="deleteNote(note.id)">
            <h5 slot="title" class="card-title">{{note.title}}</h5>
            <h6 slot="subtitle" class="card-subtitle mb-2 text-muted">{{note.subtitle}}</h6>
            <p slot="text" class="card-text">{{note.text}}</p>
          </note-card>
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
      titleInput: '',
      subtitleInput: '',
      textInput: '',
      notes: [
        {id:1, title:'Card Title', subtitle:'Card subtitle', text:'Some quick example text to build on the card title and make up the bulk of the card\'s content.'}
      ]
    }
  },
  methods:{
    addNote(){
      if(this.notes.length !== 10){
        this.notes.push({
          id:this.notes.length + 1,
          title: this.titleInput,
          subtitle: this.subtitleInput,
          text: this.textInput
        })
        this.emptyInputs();  
      }
    },
    emptyInputs(){
      this.titleInput = '';
      this.subtitleInput = '';
      this.textInput = '';
    },
    deleteNote(noteId){
      this.notes.forEach( function(element, index, array) {
        if (element.id == noteId) {
          array.splice(index,1)
        }
      });
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
