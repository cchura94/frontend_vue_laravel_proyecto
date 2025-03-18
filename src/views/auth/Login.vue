<template>
    <h1>Ingresar</h1>

    <label for="">Ingrese Correo:</label>
    <input type="email" v-model="credenciales.email">
    <br>
    <label for="">Ingrese Contraseña:</label>
    <input type="password" v-model="credenciales.password">
    <br>
    <button @click="funIngresar()">Ingresar</button>
    <br>
    {{ credenciales }}
    <br>
    {{ respuesta }}
    
</template>
<script setup>
import { ref } from 'vue';
import authService from '../../services/auth.service';

const credenciales = ref({email: "", password: ""});
const respuesta = ref();

async function funIngresar(){
    const res = await authService.login(credenciales.value);

    respuesta.value = res.data
}
</script>