<template>
    <v-row>
       <v-data-table>
        :headers="headers"
        :items="usuarios"
        :items-per-page="5"
        :class="elevation-1"
       </v-data-table>
    </v-row>
</template>

<script>
export default{
    data () {
        return {
            usuarios: [],
            headers: [
                {
                    text: 'Nombre',
                    aling: 'center',
                    sortable: true,
                    value:'name'
                },
                {
                    text: 'correo',
                    aling: 'center',
                    sortable: true,
                    value:'lastname'
                },
                {
                    text: 'fecha',
                    aling: 'center',
                    sortable: true,
                    value:'date'
                }
            ]
        }
    }, 
    methods:{
        async loadUsers(){ 
        const config = {
            headers: {
                'Content-type': 'application/json;charset=UTF-8'
                
            }
        }
        {
            await this.$axios.get('/user/getallusers', config)
            .then((res) => 
            {
                console.log('res', res)
                if(res.data.message === 'Usuarios'){
                    this.usuarios = res.data.data
                }
            })
            .catch((error) =>{
                console.log('error', error)
            })
        }
    }
}
}
</script>

