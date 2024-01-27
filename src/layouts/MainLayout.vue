<template>
  <q-layout view="lHh Lpr lFf">
    <q-page-container>
      <login-page v-if="!loginPassed" />
      <dashboard-panel v-if="loginPassed" />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { defineComponent, onMounted, ref } from "vue";
import LoginPage from "pages/login/LoginPage.vue";
import DashboardPanel from "pages/DashboardPanel.vue";
const loginPassed = ref(null);

onMounted(() => {
  getSession();
});

function getSession() {
  if (sessionStorage.getItem("token")) {
    console.log("Session: " + sessionStorage.getItem("token"));
    loginPassed.value = true;
  } else {
    loginPassed.value = false;
  }
}
</script>
, DashboardPanel
