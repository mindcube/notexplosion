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
                    <Note v-for="(note, index) in notes" 
                          v-bind:key="index" 
                          v-bind:note="note"
                          v-bind:colors="colors"
                          v-on:remove-note="removeNote">
                    </Note>
                </v-layout>
            </v-container>      
        </v-content>
        <v-dialog v-model="modal"
                  max-width="500px"
                  persistent>
            <v-card>
                <v-card-title class="headline">Add a new note</v-card-title>

                <v-form ref="form">
                    <v-card-text>
                        <v-container grid-list-md>
                            <v-layout wrap>
                                <v-flex xs12>
                                    <v-text-field label="Title" 
                                                v-model="input.title"
                                                required>
                                    </v-text-field>
                                </v-flex>
                                <v-flex xs12>
                                    <v-textarea name="input-7-1"
                                                label="Note"
                                                v-model="input.note"
                                                hint="Enter your note here!">
                                    </v-textarea>
                                </v-flex>
                                <v-flex xs12>
                                    <v-select name="input-7-1"
                                                label="Color"
                                                v-model="input.color"
                                                :items="colors">
                                    </v-select>
                                </v-flex>
                            </v-layout>
                        </v-container>
                    </v-card-text>
            
                    <v-card-actions>
                        <v-spacer></v-spacer>
                        <v-btn color="green darken-1"
                               flat="flat"
                               @click="modal = false">
                            Cancel
                        </v-btn>
                        <v-btn color="green darken-1"
                               flat="flat"
                               @click="submit">
                            Create Note
                        </v-btn>
                    </v-card-actions>
                </v-form>
            </v-card>
        </v-dialog>
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
            notes: [],
            input: {
                note: '',
                title: '',
                color: 'white'
            },
            colors: [
                { 
                    text: 'white',
                    value: 'white' 
                },
                { 
                    text: 'red', 
                    value: '#FFEBEE' 
                },
                { 
                    text: 'pink',
                    value: '#FCE4EC' 
                },
                { 
                    text: 'purple',
                    value: '#F3E5F5' 
                },
                { 
                    text: 'indigo',
                    value: '#E8EAF6' 
                },
            ]
        }
    },

    methods: {
        submit() {
            this.notes.push({
                title: this.input.title,
                note: this.input.note,
                color: this.input.color
            })

            this.clear()
            this.modal = false
        },

        clear() {
            this.input.title = ''
            this.input.note = ''
            this.input.id = null
        },

        removeNote(note) {
            const noteIndex = this.notes.indexOf(note);

            this.notes.splice(noteIndex, 1);
        }
    }
}
</script>
