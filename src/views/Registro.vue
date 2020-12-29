<template>
    <div>
        <h1>Formulario de Registro</h1>
        <form>
            <div class="mb-3  col-12 col-sm-12 col-md-6 col-lg-4 col-xl-4 mx-auto" @submit.prevent="registrarNuevoUsuario">
                <label for="exampleInputFoto" class="form-label">Sube tu Avatar</label>
                <input type="text" class="form-control" id="exampleInputFoto" v-model="photoURL">
            </div>
            <div class="mb-3  col-12 col-sm-12 col-md-6 col-lg-4 col-xl-4 mx-auto">
                <label for="exampleInputNombre" class="form-label">Nombre</label>
                <input type="text" class="form-control" id="exampleInputNombre" v-model="displayName">
            </div>
            <div class="mb-3  col-12 col-sm-12 col-md-6 col-lg-4 col-xl-4 mx-auto">
                <label for="exampleInputEmail1" class="form-label">Correo Electrónico</label>
                <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" v-model="email">
            </div>
            <div class="mb-3  col-12 col-sm-12 col-md-6 col-lg-4 col-xl-4 mx-auto">
                <label for="exampleInputPassword1" class="form-label">Password</label>
                <input type="password" class="form-control" id="exampleInputPassword1" v-model="password">
            </div>
            <div class="mb-3  col-12 col-sm-12 col-md-6 col-lg-4 col-xl-4 mx-auto">
                <button type="submit" class="btn btn-primary">Ingresar</button>
            </div>
        </form>
    </div>
</template>

<script>


export default {
    name: 'Registro',
    data(){
        return {
           
        }
    },
    methods: {
        registrarNuevoUsuario(){
            this.$store.dispatch('registrandoNuevoUsuario');
        }
        
     },
}
</script>

<style>

</style>