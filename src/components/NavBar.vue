<template>
    <div class="my-5">
        <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">Navbar</a>
            <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav">
                <li class="nav-item">
                <router-link to="/" class="nav-link active">Home</router-link> 
                </li>
                <li class="nav-item">
                <router-link to="/datosPacientes" class="nav-link active">Datos Pacientes</router-link> 
                </li>
                <li class="nav-item">
                <router-link to="/listadoUsuarios" class="nav-link active">Listado Usuarios</router-link> 
                </li>
                <li class="nav-item">
                <router-link to="/registro" class="nav-link active">Registrarse</router-link> 
                </li>
                <li class="nav-item">
                <router-link to="/login" class="nav-link active" :class="{name: 'Login'}">Login</router-link> 
                </li>
                <li class="nav-item">
                <a class="nav-link logOut" disabled="false" @click.prevent="signOut">Sign Out</a> 
                </li>
            </ul>
            </div>
        </div>
        </nav>
    </div>
</template>

<script>
import firebase from 'firebase';
import Swal from 'sweetalert2';

export default {
    name: 'NavBar',
    methods: {
        signOut(){
            firebase.auth().signOut().then(()=> {
                   Swal.fire({
                title: 'Tu sesión se ha cerrado exitosamente',
                showClass: {
                    popup: 'animate__animated animate__fadeInDown'
                },
                hideClass: {
                    popup: 'animate__animated animate__fadeOutUp'
                }
                })
            }).catch((error)=> {
                console.error(error);
                Swal.fire({
                    icon: 'error',
                    title: 'Oops...',
                    text: 'Ha ocurrido un error, intentalo nuevamente'
                })
            });
        }
    },
}
</script>

<style>

</style>