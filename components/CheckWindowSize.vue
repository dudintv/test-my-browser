<script setup lang="ts">
import { onMounted, ref, reactive } from "vue";

const innerSizes = ref({});
const outerSizes = ref({});

function onResize() {
  innerSizes.value = { width: window.innerWidth, height: window.innerHeight };
  outerSizes.value = { width: window.outerWidth, height: window.outerHeight };
}

onMounted(() => {
  onResize();
  window.addEventListener("resize", onResize);
});
</script>

<template>
  <h1>window test</h1>
  <p>innerSizes = {{ innerSizes }}</p>
  <p>outerSizes = {{ outerSizes }}</p>
</template>

<style lang="scss" scoped></style>
