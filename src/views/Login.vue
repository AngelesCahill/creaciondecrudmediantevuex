<template>
    <div>
        <form>
            <div class="mb-3  col-12 col-sm-12 col-md-6 col-lg-4 col-xl-4 mx-auto" @submit.prevent="ingresar">
                <label for="exampleInputFoto" class="form-label">Sube tu Avatar</label>
                <input type="text" class="form-control" id="exampleInputFoto" v-model="photoURL">
            </div>
            <div class="mb-3  col-12 col-sm-12 col-md-6 col-lg-4 col-xl-4 mx-auto">
                <label for="exampleInputNombre" class="form-label">Email address</label>
                <input type="text" class="form-control" id="exampleInputNombre" v-model="displayName">
            </div>
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

    export default {
        name: 'Login',
        data(){
            return {
                nombre: '',
                email: '',
                password: '',
                urlPhoto: ''
            }
        },
        methods: {
            ingresar(){
               if (this.email && this.password.length >= 6) {
                // metodo que permite ingresar con usuario(correo electrónico) y contraseña
            firebase.auth().signInWithEmailAndPassword(this.email, this.password)
                .then((result) => {
                    console.log(result.user.uid);
                    console.log(result.user.photoURL);
                    console.log(result.user.email);
                    console.log(result.user.displayName);
                    console.log(result.user.emailVerified);
                    console.log("login");
                    this.$router.push({name: 'Home'}); // enviamos al usuario a la vista de home
                })
                .catch((error) => {
                    console.error(error.code);
                    console.error(error.message);
                });
            } else {
            console.log("no se puede");
            }
        }
        }
    }
</script>

<style>

</style>