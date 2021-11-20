<template>
                <v-dialog
            v-model="dialog"
            persistent
            max-width="290"
            >
            <template v-slot:activator="{ on, attrs }">
                <v-icon
                v-bind="attrs"
                v-on="on"></v-icon>
                <!-- <v-icon
                v-bind="attrs"
                v-on="on">mdi-trash-can-outline</v-icon> -->
            </template>
            <v-card elevation="3" >
                <v-card-title></v-card-title>
                <v-card-text>
                <v-spacer></v-spacer>
                    <p class="text-danger">Eliminar</p>
                    Al eliminar tambien se eliminaran las listas y tarea relacionadas con este panel
                    el id #{{id}}
                </v-card-text>
                <v-card-actions>
                <v-spacer></v-spacer>
                    <v-icon @click="dialog = false">mdi-check-bold</v-icon>
                    <v-icon @click="deleted()" >mdi-close-thick</v-icon>
                </v-card-actions>
            </v-card>
            </v-dialog>
</template>

<script>
export default {
    props:{
        id:String,
        name:String
    },
    data() {
        return{
            dialog: false,
            notifications: false,
            sound: true,
            widgets: false,
        }
    },
    methods:{
        deleted(){
            console.log('funcion eliminar board' + this.id)
            this.dialog = false
        }
    }
}
</script>
<style scoped>
.v-application .justify-center {
    justify-content: end !important;
    margin: 0;
    padding: 0;
}
</style>