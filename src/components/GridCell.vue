<script lang="ts">
export default {
  name: 'GridCell',
};
</script>

<script setup lang="ts">
import { ICellRendererParams } from '@ag-grid-community/core';
interface GridCellTooltipInterface extends ICellRendererParams {
  name?: string;
}

defineProps<{ params: GridCellTooltipInterface }>();
</script>

<template>
  <span class="cell">{{ params.name }} {{params.value}}</span>
</template>

<style>
.cell {
  color: red;
}
</style>
