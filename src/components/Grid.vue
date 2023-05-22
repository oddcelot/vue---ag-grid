<script lang="ts">
export default {
  name: "Grid",
  components: {
    AgGridVue,
    GridCell,
    GridCellEditor,
    GridCellEditorClassic,
    GridCellEditorWrapper,
  },
};
</script>

<script setup lang="ts">
import "ag-grid-community/styles/ag-grid.css";
import "ag-grid-community/styles/ag-theme-alpine.css";
import { AgGridVue } from "ag-grid-vue3";
import GridCell from "./GridCell.vue";
import GridCellEditor from "./GridCellEditor.vue";
import GridCellEditorClassic from "./GridCellEditorClassic.vue";
import GridCellEditorWrapper from "./GridCellEditorWrapper.vue";
import { ColDef } from "ag-grid-community";

const columnDefs: ColDef[] = [
  {
    headerName: "Make",
    field: "make",
    editable: true,
    cellRenderer: "GridCell",
    cellRendererParams: { name: "custom" },
    cellEditor: "GridCellEditor",
  },
  {
    headerName: "Model",
    field: "model",
    editable: true,
    cellEditor: "GridCellEditorWrapper",
  },
  {
    headerName: "Price",
    field: "price",
    cellRenderer: "GridCellEditor",
    editable: true,
    cellEditor: "GridCellEditorClassic",
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
    <AgGridVue
      style="height: 200px"
      class="ag-theme-alpine"
      :columnDefs="columnDefs"
      :rowData="rowData"
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
