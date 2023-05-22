<script lang="ts">
export default {
  name: "GridCellEditor",
};
</script>

<script setup lang="ts">
import { ref, onMounted, nextTick } from "vue";
import { ICellRendererParams } from "@ag-grid-community/core";
interface GridCellTooltipInterface extends ICellRendererParams {
  name?: string;
}

const props = defineProps<{ params: GridCellTooltipInterface }>();

const value = ref(props.params.value);

const input = ref<HTMLInputElement>();

/* Component Editor Lifecycle methods */
// the final value to send to the grid, on completion of editing
const getValue = () => {
  // this simple editor doubles any value entered into the input
  return value.value * 2;
};

// Gets called once before editing starts, to give editor a chance to
// cancel the editing before it even starts.
const isCancelBeforeStart = () => {
  return false;
};

// Gets called once when editing is finished (eg if Enter is pressed).
// If you return true, then the result of the edit will be ignored.
const isCancelAfterEnd = () => {
  // our editor will reject any value greater than 1000
  return value.value > 1000;
};

onMounted(() => {
  // focus on the input field once editing starts
  nextTick(() => {
    input.value?.focus();
  });

  // console.log(this);
});

defineExpose({
  getValue,
  isCancelBeforeStart,
  isCancelAfterEnd,
});
</script>

<template>
  <div class="cell-editor">
    <input type="text" v-model="value" ref="input" style="width: 100%" />
  </div>
</template>

<style>
.cell-edtior span {
  color: red;
}
</style>
