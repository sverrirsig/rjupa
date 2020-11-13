<template>
    <v-card
        elevation="8"
    >
        <v-card-title class="justify-center headline">
            {{time.time}}
        </v-card-title>
        <v-card-subtitle align="center">
            {{time.text}}
        </v-card-subtitle>
    </v-card>
</template>

<script>
export default {
    props: ["time"],
}
</script>