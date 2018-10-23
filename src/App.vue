<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>Note</span>
        <span class="font-weight-light">xplosion</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn icon @click="modal = true">
          <v-icon>add</v-icon>
      </v-btn>
    </v-toolbar>

    <v-content>
      <v-container fluid grid-list-md>
        <v-layout row wrap>
          <Note v-for="note in notes" 
                v-bind:key="note.id" 
                :title="note.title" 
                :note="note.note" 
                :id="note.id">
          </Note>
          <v-dialog
            v-model="modal"
            max-width="500px"
            persistent
          >
            <v-card>
              <v-card-title class="headline">Add a new note</v-card-title>
      
              <v-form ref="form">
                <v-card-text>
                  <v-container grid-list-md>
                    <v-layout wrap>
                      <v-flex xs12>
                        <v-text-field
                          label="Title" 
                          v-model="input.title"
                          required
                        ></v-text-field>
                      </v-flex>
                      <v-flex xs12>
                        <v-textarea
                          name="input-7-1"
                          label="Note"
                          v-model="input.note"
                          hint="Enter your note here!"
                        ></v-textarea>
                      </v-flex>
                    </v-layout>
                  </v-container>
                </v-card-text>
        
                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn
                    color="green darken-1"
                    flat="flat"
                    @click="modal = false"
                  >
                    Cancel
                  </v-btn>
                  <v-btn
                    color="green darken-1"
                    flat="flat"
                    @click="submit"
                  >
                    Agree
                  </v-btn>
                </v-card-actions>
              </v-form>
            </v-card>
          </v-dialog>
        </v-layout>
      </v-container>      
    </v-content>
  </v-app>
</template>

<script>
import Note from './components/Note'

export default {
  name: 'App',
  components: {
    Note
  },
  data () {
    return {
      modal: false,
      input: {
        note: '',
        title: ''
      },
      notes: []
    }
  },

  methods: {
    submit() {
      this.notes.push({
        title: this.input.title,
        note: this.input.note
      })

      this.clear()
      this.modal = false
    },

    clear() {
      this.input.title = ''
      this.input.note = ''
    }
  }
}
</script>
