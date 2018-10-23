<template>
    <v-flex xs12 sm8 md4>
        <v-card :color="note.color" class="ma-3">
            <v-responsive :aspect-ratio="16/9">
                <div v-if="isEditing">
                    <v-card-text>
                        <v-container grid-list-md>
                            <v-layout wrap>
                                <v-flex xs12>
                                    <v-text-field label="Title" 
                                                v-model="note.title"
                                                required>
                                    </v-text-field>
                                </v-flex>
                                <v-flex xs12>
                                    <v-textarea name="input-7-1"
                                                label="Note"
                                                v-model="note.note"
                                                hint="Enter your note here!">
                                    </v-textarea>
                                </v-flex>
                                <v-flex xs12>
                                    <v-select name="input-7-1"
                                                label="Color"
                                                v-model="note.colors"
                                                hint="Enter your note here!">
                                    </v-select>
                                </v-flex>
                            </v-layout>
                        </v-container>
                    </v-card-text>
                    <v-card-actions>
                        <v-spacer></v-spacer>
                        <v-btn color="green darken-1"
                               flat="flat"
                               @click="isEditing = false">
                            Close
                        </v-btn>
                    </v-card-actions>
                </div>
                <div v-else>
                    <v-toolbar color="blue" dark>
                        <v-toolbar-title>{{ note.title }}</v-toolbar-title>
                        <v-spacer></v-spacer>
                        <v-btn icon  @click="isEditing = true">
                            <v-icon>edit</v-icon>
                        </v-btn>
                        <v-btn icon @click="removeNote(note)">
                            <v-icon>close</v-icon>
                        </v-btn>
                    </v-toolbar>
                    <v-card-text color="blue">
                        {{ note.note }}
                    </v-card-text>
                </div>
            </v-responsive>
        </v-card>
    </v-flex>
</template>

<script>
export default {
    props: [
        'note'
    ],

    data() {
        return {
            isEditing: false,
        };
    },

    methods: {
        removeNote(note) {
            this.$emit('remove-note', note);
        }
    }
}
</script>

<style>

</style>
