<template>
    <v-flex xs12 sm8 md4>
        <v-card color="white" class="ma-3">
            <v-responsive :aspect-ratio="16/9">
                <v-toolbar color="blue" dark>
                    <v-toolbar-title>{{ title }}</v-toolbar-title>
                    <v-spacer></v-spacer>
                    <v-btn icon>
                        <v-icon>close</v-icon>
                    </v-btn>
                </v-toolbar>
                <v-card-text color="blue">
                    {{ note }}
                </v-card-text>
            </v-responsive>
        </v-card>
    </v-flex>
</template>

<script>
export default {
    props: [
        'id',
        'title',
        'note'
    ]
}
</script>

<style>

</style>
