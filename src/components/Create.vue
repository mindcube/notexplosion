<template>
    <v-flex xs12 sm8 md4>
        <v-card class="ma-3 text-xs-center" flat>
            <v-btn icon>
                <v-icon x-large>note_add</v-icon>
            </v-btn>
        </v-card>
    </v-flex>
</template>

<script>
export default {
    props: [
        'id',
        'title',
        'text'
    ]
}
</script>

<style>

</style>
