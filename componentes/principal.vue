<template>
    <v-col cols="12">
        <v-row>
            <v-data-table>
                :headers="headers"
                :items="usuarios"
                :items-per-page="5"
                :class="elevation-1"
            </v-data-table>
        </v-row>
    </v-col>
    <v-row class="renglon">
        <v-btn>
            Agregar Nuevo Usuarios
        </v-btn>
    </v-row>
    <v-dialog v-model="openDialog" width="800" height="500" persistent>
        <v-card>Agregar datos del usuarios</v-card>
        <v-card-text>
            //Nuxt👻👻👻
        </v-card-text>

        <v-form ref="formRegistro">
            <v-text-field type="text" aria-placeholder="Name:" label="name"></v-text-field>
        </v-form>

        <v-form ref="formRegistro">
            <v-text-field type="text" aria-placeholder="LastName:" label="name"></v-text-field>
        </v-form>

        <v-form ref="formRegistro">
            <v-text-field type="text" aria-placeholder="Email:" label="name"></v-text-field>
        </v-form>

        <v-form ref="formRegistro">
            <v-text-field type="text" aria-placeholder="Password:" label="name"></v-text-field>
        </v-form>

        <v-card-actions style="width:100%; display:flex; flex-directions: column; ">
            <v-row style="width: 100%; margin-top:5px; margin-bottom: 10px;"></v-row>
            <v-btn black color="green" @click="openDialog = false">
                Cancelar
            </v-btn>
            <v-btn black color="green" @click="openDialog = false">Registrar</v-btn>

        </v-card-actions>


    </v-dialog>

</template>

<script>
export default {
    data() {
        return {
            usuarios: [],
            headers: [
                {
                    text: 'Nombre',
                    aling: 'center',
                    sortable: true,
                    value: 'name'
                },
                openDialog: false,
                name: '',
                lastname: '',
                email: '',
                password: '',
                {
                    text: 'correo',
                    aling: 'center',
                    sortable: true,
                    value: 'lastname'
                },
                {
                    text: 'fecha',
                    aling: 'center',
                    sortable: true,
                    value: 'date'
                }
            ]
        }
    },
    methods: {
        async loadUsers() {
            const config = {
                headers: {
                    'Content-type': 'application/json;charset=UTF-8'

                }
            }
            {
                await this.$axios.get('/user/getallusers', config)
                    .then((res) => {
                        console.log('res', res)
                        if (res.data.message === 'Usuarios') {
                            this.usuarios = res.data.data
                        },
                        openDialog: true;
                    })
                    .catch((error) => {
                        console.log('error', error)
                    }),
                    this.openDialog: true;
            }

            const usuarioNuevo = {
                name: this.name,
                lastname: this.lastname,
                email: this.email,
                password = this.password
            }
            await this.$axios.post('/user/register', usuarioNuevo, config)
            .then((res) =>{
                console.log('res', res)
            })
            .catch((error) =>{
                console.log('error', error)
            })
        }
    }
}
</script>

<style scoped>
.renglon {
    width: 100%;
    margin-top: 20px;
    margin-bottom: 20px;
}
</style>

