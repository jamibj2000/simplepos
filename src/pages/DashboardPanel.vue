<template>
  <section>
    <div class="q-pa-sm">
      <div
        class="q-pa-sm bg-white rounded-borders login-box-shade"
        style="display: flex; flex-direction: column"
      >
        <big class="text-center"> Panel administrativo </big>
      </div>
      <section class="q-pa-lg bg-accent">
        <!-- HERE GOES THE MODULES -->
        <PurchaseModule />
      </section>
    </div>
  </section>
</template>

<script setup>
import { onMounted, ref } from "vue";
import PurchaseModule from "../components/PurchaseModule.vue";

// function getProducts() {
//   axios
//     .get("http://localhost:8080/products")
//     .then(function (response) {
//       productsList.value = response.data;
//     })
//     .catch(function (error) {
//       console.log(error);
//     });
// }

onMounted(() => {
  console.log("Mounted- Dashboard Panel");
});
</script>
