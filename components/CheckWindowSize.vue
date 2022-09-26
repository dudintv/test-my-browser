<script setup lang="ts">
import { onMounted, ref, reactive, computed } from "vue";

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

const isHugeFiller = ref(false);
const fillerHeight = computed(() => (isHugeFiller.value ? "150vh" : "30vh"));
</script>

<template>
  <h1>window test</h1>
  <p>innerSizes = {{ innerSizes }}</p>
  <p>outerSizes = {{ outerSizes }}</p>
  <input type="text" name="test" id="test-input-id" />
  <div class="filler" :style="`height: ${fillerHeight}`" @click="isHugeFiller = !isHugeFiller">
    filler: {{ fillerHeight }}
  </div>
</template>

<style lang="scss" scoped>
.filler {
  width: 100%;
  background-color: coral;
  border: 1px solid rebeccapurple;
}

input {
  width: 90%;
  font-size: 2rem;
  padding: 0.5rem 1rem;
  margin-bottom: 1rem;
}
</style>
