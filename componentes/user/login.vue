<template>
    <v-card > </v-card>
    <v-card>
<v-card-title>login</v-card-title>
    </v-card>
    <v-form v-model="formularioValido">
        <v-text-field label="correo" placeholder="correo">
            v-model="correo"
        </v-text-field>
    </v-form>
 <v-card-actions>
    Boton para iniciar sesion
 </v-card-actions>
</template>

<script>
exports default{
    Data(){
        return{
                formularioValido:false,
                correo:false
        }
    }
}
</script>
<style scoped>

.cardlogin{
    background-color: bisque;
    border-radius: 10px;
    width: 500px;
    height: auto;
}


</style>