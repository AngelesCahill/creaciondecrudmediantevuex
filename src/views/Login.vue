<template>
    <div>
        <form @submit.prevent="loginUser">
            <div class="mb-3  col-12 col-sm-12 col-md-6 col-lg-4 col-xl-4 mx-auto">
                <label for="exampleInputEmail1" class="form-label">Email address</label>
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
import firebase from 'firebase';
import Swal from 'sweetalert2';

export default {
    name: 'Login',
    data(){
        return {
            email: '',
            password: '',
        }
    },
    methods: {
        loginUser(){
            if (this.email && this.password.length >= 6) {
                firebase.auth().signInWithEmailAndPassword(this.email, this.password)
                .then((result) => {
                    console.log(result.user.uid);
                    console.log(result.user.displayName);
                    console.log(result.user.email);
                    console.log(result.user.emailVerified);
                    console.log(result.user.photoURL);
                    Swal.fire('Bienvenido'+' '+this.email);
                    this.$router.push({name:'Home'})
               
                })
                .catch((error) => {
                    console.error(error.code);
                    console.error(error.message);
                });
                } else {
                    Swal.fire({
                        icon: 'error',
                        title: 'Oops...',
                        text: 'Debes registrarte primero',
                })
            }
        
        }
    },
}
</script>

<style>

</style>