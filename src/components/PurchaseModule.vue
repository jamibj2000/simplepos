<template>
  <span class=""><big>COMPRAS</big></span>
  <span class="rounded-borders text-blue bg-red" style="height: 100px !important">
    <div class="simple-box-shade q-pa-lg">
      <div class="row">
        <div class="col-12">Listado de compras</div>
        <div class="row flex-center col-12" style="display: flex; flex-direction: column">
          <div class="q-pa-md">
            <q-table
              flat
              bordered
              title="Treats"
              :rows="rows"
              :columns="productList"
              row-key="id"
              :filter="filter"
              :loading="loading"
            >
              <template v-slot:top>
                <q-input dense debounce="300" color="primary" v-model="filter">
                  <template v-slot:append>
                    <q-icon name="search" />
                  </template>
                </q-input>
              </template>
            </q-table>
          </div>
        </div>
      </div>
    </div>
  </span>
</template>
<script setup>
import { ref } from "vue";

const productList = [
  {
    name: "productName",
    required: true,
    label: "Producto",
    align: "left",
    field: (row) => row.name,
    format: (val) => `${val}`,
    sortable: true,
  },
  {
    name: "productAmount",
    align: "center",
    label: "Cantidad",
    field: "productAmount",
    sortable: true,
  },
  {
    name: "price",
    align: "center",
    label: "Precio",
    field: "price",
    sortable: true,
  },
];

const originalRows = [
  {
    name: "Frozen Yogurt",
    productAmount: 159,
    price: 6.0,
  },
  {
    name: "Ice cream sandwich",
    productAmount: 237,
    price: 9.0,
  },
  {
    name: "Eclair",
    productAmount: 262,
    price: 16.0,
  },
];

const loading = ref(false);
const filter = ref("");
const rowCount = ref(10);
const rows = ref([...originalRows]);

function setProduct() {}
</script>
