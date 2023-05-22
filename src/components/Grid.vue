<script lang="ts">
export default {
  name: "Grid",
  components: {
    AgGridVue,
    GridCell,
    GridCellEditor,
  },
};
</script>

<script setup lang="ts">
import { usePreferredDark } from "@vueuse/core";
import "ag-grid-community/styles/ag-grid.css";
import "ag-grid-community/styles/ag-theme-alpine.css";
import { AgGridVue } from "ag-grid-vue3";
import GridCell from "./GridCell.vue";
import GridCellEditor from "./GridCellEditor.vue";
import { ColDef, GridReadyEvent } from "ag-grid-community";

const columnDefs: ColDef[] = [
  {
    headerName: "Make",
    field: "make",
    cellRenderer: "GridCell",
    cellRendererParams: { name: "custom" },
  },
  {
    headerName: "Model",
    field: "model",
  },
  {
    headerName: "Price",
    field: "price",
    editable: true,
    cellEditor: "GridCellEditor",
  },
];

const rowData = [
  { make: "Toyota", model: "Celica", price: 35000 },
  {
    make: "Ford",
    model: "Mondeo",
    price: 32000,
  },
  { make: "Porsche", model: "Boxster", price: 72000 },
];
</script>

<template>
  <div class="grid">
    <pre>{{ usePreferredDark() }}</pre>
    <AgGridVue
      class="ag-theme-alpine"
      :class="{ 'ag-theme-alpine-dark': usePreferredDark().value }"
      :columnDefs="columnDefs"
      :rowData="rowData"
      @grid-ready="
        ($event: GridReadyEvent<typeof rowData>) => {
          $event.api.sizeColumnsToFit();
        }
      "
      dom-layout="autoHeight"
    >
    </AgGridVue>
  </div>
</template>

<style>
.grid {
  width: 100%;
  display: block;
}
</style>
