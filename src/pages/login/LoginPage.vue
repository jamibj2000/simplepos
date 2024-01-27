<template>
  <section class="bg-accent row flex-center flex-column" style="min-height: 100vh">
    <div class="q-pa-md">
      <div
        class="q-pa-md bg-white rounded-borders login-box-shade"
        style="display: flex; flex-direction: column"
      >
        <big class="text-center"> Iniciar sesión </big>
        <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
          <q-input
            v-model="username"
            label="Nombre de usuario *"
            hint="Nombre de usuario"
            class="q-pa-md"
            lazy-rules
            :rules="[
              (val) =>
                (val && val.length > 0) || 'Por favor, escribe su nombre de usuario',
            ]"
          />

          <q-input
            class="q-pa-md"
            type="password"
            v-model="password"
            label="Tu contraseña *"
          />

          <q-toggle v-model="accept" label="Acepto los terminos y condiciones" />

          <div class="row flex-center">
            <q-btn label="Ingresar" type="submit" color="primary" @click="login()" />
            <!-- <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" /> -->
          </div>
        </q-form>
      </div>
    </div>
  </section>
</template>

<script setup>
import axios from "axios";
import { onMounted, ref } from "vue";
const username = ref(null);
const password = ref(null);
const accept = ref(false);
// const loginAcepted = ref(false);

onMounted(() => {
  console.log("Mounted- Login Page");
});

function login() {
  axios
    .get("http://localhost:8080/login")
    .then(function (response) {
      sessionStorage.setItem("token", response.data);
      window.location.href = "/";
    })
    .catch(function (error) {
      console.log(error);
    });
}
</script>
